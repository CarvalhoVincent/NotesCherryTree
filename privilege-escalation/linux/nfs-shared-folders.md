# ↔ NFS Shared folders

Privilege escalation vectors are not confined to internal access. Shared folders and remote management interfaces such as SSH and Telnet can also help you gain root access on the target system. Some cases will also require using both vectors, e.g. finding a root SSH private key on the target system and connecting via SSH with root privileges instead of trying to increase your current user’s privilege level.

Another vector that is more relevant to CTFs and exams is a misconfigured network shell. This vector can sometimes be seen during penetration testing engagements when a network backup system is present.

NFS (Network File Sharing) configuration is kept in the /etc/exports file. This file is created during the NFS server installation and can usually be read by users.\


<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

The critical element for this privilege escalation vector is the “no\_root\_squash” option you can see above. By default, NFS will change the root user to nfsnobody and strip any file from operating with root privileges. If the “no\_root\_squash” option is present on a writable share, we can create an executable with SUID bit set and run it on the target system.

We will start by enumerating mountable shares from our attacking machine.\


<div align="left">

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

</div>

We will mount one of the “no\_root\_squash” shares to our attacking machine and start building our executable.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

As we can set SUID bits, a simple executable that will run /bin/bash on the target system will do the job.

<div align="left">

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

</div>

Once we compile the code we will set the SUID bit.

<div align="left">

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

</div>

You will see below that both files (nfs.c and nfs are present on the target system. We have worked on the mounted share so there was no need to transfer them).

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Notice the nfs executable has the SUID bit set on the target system and runs with root privileges

\-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Files created via NFS inherit the **remote**¬†user's ID. If the user is root, and root squashing is enabled, the ID will instead be set to the "nobody" user.\
Check the NFS share configuration on the Debian VM:\
`cat /etc/exports`

\
Note that the **/tmp** share has root squashing disabled.\
On your Kali box, switch to your root user if you are not already running as root:\
`sudo su`\
Using Kali's root user, create a mount point on your Kali box and mount the **/tmp** share (update the IP accordingly):

```bash
mkdir /tmp/nfs
mount -o rw,vers=3 10.10.10.10:/tmp /tmp/nfs
```

Still using Kali's root user, generate a payload using **msfvenom** and save it to the mounted share (this payload simply calls /bin/bash):

```bash
msfvenom -p linux/x86/exec CMD="/bin/bash -p" -f elf -o /tmp/nfs/shell.elf
```

Still using Kali's root user, make the file executable and set the SUID permission:\
`chmod +xs /tmp/nfs/shell.elf`\
Back on the Debian VM, as the low privileged user account, execute the file to gain a root shell:\
`/tmp/shell.elf`

# 🛣 PATH

```bash
echo $PATH
find / -writable 2>/dev/null
export PATH=/tmp:$PATH
```

If a folder for which your user has write permission is located in the path, you could potentially hijack an application to run a script. PATH in Linux is an environmental variable that tells the operating system where to search for executables. For any command that is not built into the shell or that is not defined with an absolute path, Linux will start searching in folders defined under PATH. (PATH is the environmental variable we're talking about here, path is the location of a file).

Typically the PATH will look like this:\


<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

If we type “thm” to the command line, these are the locations Linux will look in for an executable called thm. The scenario below will give you a better idea of how this can be leveraged to increase our privilege level. As you will see, this depends entirely on the existing configuration of the target system, so be sure you can answer the questions below before trying this.\
1\. What folders are located under $PATH\
2\. Does your current user have write privileges for any of these folders?\
3\. Can you modify $PATH?\
4\. Is there a script/application you can start that will be affected by this vulnerability?\
For demo purposes, we will use the script below:

<div align="left">

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

</div>

This script tries to launch a system binary called “thm” but the example can easily be replicated with any binary.

We compile this into an executable and set the SUID bit.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

Our user now has access to the “path” script with SUID bit set.

<div align="left">

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

</div>

Once executed “path” will look for an executable named “thm” inside folders listed under PATH.

If any writable folder is listed under PATH we could create a binary named thm under that directory and have our “path” script run it. As the SUID bit is set, this binary will run with root privilege

A simple search for writable folders can done using the “`find / -writable 2>/dev/null`” command. The output of this command can be cleaned using a simple cut and sort sequence.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Some CTF scenarios can present different folders but a regular system would output something like we see above.\
Comparing this with PATH will help us find folders we could use.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

We see a number of folders under /usr, thus it could be easier to run our writable folder search once more to cover subfolders.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

An alternative could be the command below.

```bash
find / -writable 2>/dev/null | cut -d "/" -f 2,3 | grep -v proc | sort -u
```

We have added “grep -v proc” to get rid of the many results related to running processes.

Unfortunately, subfolders under /usr are not writable

The folder that will be easier to write to is probably /tmp. At this point because /tmp is not present in PATH so we will need to add it. As we can see below, the “`export PATH=/tmp:$PATH`” command accomplishes this.

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

At this point the path script will also look under the /tmp folder for an executable named “thm”.\
Creating this command is fairly easy by copying /bin/bash as “thm” under the /tmp folder.

<div align="left">

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

</div>

We have given executable rights to our copy of /bin/bash, please note that at this point it will run with our user’s right. What makes a privilege escalation possible within this context is that the path script runs with root privileges.

<div align="left">

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

</div>

\--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**What is PATH?**\
PATH is an environmental variable in Linux and Unix-like operating systems which specifies directories that hold executable programs. When the user runs any command in the terminal, it searches for executable files with the help of the PATH Variable in response to commands executed by a user.

It is very simple to view the Path of the relevant user with help of the command **"echo $PATH"**.\
**How does this let us escalate privileges?**\
Let's say we have an SUID binary. Running it, we can see that it’s calling the system shell to do a basic process like list processes with "ps". Unlike in our previous SUID example, in this situation we can't exploit it by supplying an argument for command injection, so what can we do to try and exploit this?\
We can re-write the PATH variable to a location of our choosing! So when the SUID binary calls the system shell to run an executable, it runs one that we've written instead!\
As with any SUID file, it will run this command with the same privileges as the owner of the SUID file! If this is root, using this method we can run whatever commands we like as root!

Going back to our local ssh session, not the netcat root session, you can close that now, let's exit out of root from our previous task by typing **"exit"**. Then use **"su"** to swap to user5, with the password **"password"**

Let's go to user5's home directory, and run the file **"script"**. What command do we think that it's executing?

Now we know what command to imitate, let's change directory to **"tmp"**.&#x20;

Now we're inside tmp, let's create an imitation executable. The format for what we want to do is:

echo "\[whatever command we want to run]" > \[name of the executable we're imitating]

What would the command look like to open a bash shell, writing to a file with the name of the executable we're imitating

### echo "/bin/bash" >> ls

Great! Now we've made our imitation, we need to make it an executable. What command do we execute to do this?

### chmod +x ls

Now, we need to change the PATH variable, so that it points to the directory where we have our imitation **"ls"** stored! We do this using the command

### **export PATH=/tmp:$PATH**

Note, this will cause you to open a bash prompt every time you use **"ls"**. If you need to use **"ls"** before you finish the exploit, use **"/bin/ls"** where the real **"ls"** executable is.\
Once you've finished the exploit, you can exit out of root and use

**export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:$PATH**

to reset the PATH variable back to default, letting you use **"ls"** again!\
Now, change directory back to user5's home directory.

### Now, run the "script" file again, you should be sent into a root bash prompt! Congratulations!

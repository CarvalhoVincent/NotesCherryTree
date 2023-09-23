# 🐳 Docker

Trouver un fichier qui dit que il y a un docker

<div align="left">

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

</div>

Jenkins.txt The file consist text saying it’s running on specific IP and Port on localhost. But the IP address is different than out deployed machine, if we check ifconfig result then we get the clear idea.\


<div align="left">

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

</div>

ifconfig As you can see, there’s a docker running on target machine with 172 series IP address, so Jenkins is inside docker running on port 8080. Even if we try to access that docker IP and Port using our browser it’s not reachable. So, to access it we are going to use SSH tunneling technique to forward Jenkins ip:port to our attacker machine’s ip:port. We have exit all the logins and reverseshell. From attackers (kali linux) terminal execute below command and type the password which we retrieved from wp-save.txt file.\


<div align="left">

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

</div>

ssh tunnelTo access Jenkins, type localhost:6767 in your browser to access it.

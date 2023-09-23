# 🎩 John

pour faire une recherche:

exemples:

```bash
john --wordlist=/home/vincent/hack/wordlists/rockyou.txt analyse.txt

john --format=sha-512 --wordlist=/home/vincent/hack/wordlists/rockyou.txt

john --format=RAW-SHA512:1c362db832f3f864c8c2fe05f2002a05 --wordlist=/hom
e/vincent/hack/wordlists/rockyou.txt back.txt

```

### VI) Bruteforce de clé SSH via JohnTheRipper

JohnTheRipper est un outil très connu de bruteforce, le soucis, c’est que lui ne peut pas directement bruteforcer une clé SSH comme ça, il faut d’abord extraire son hash en utilisant un second petit outil, nommé **ssh2john** :

### Utiliser python2.7 pour eviter l'erreur de base 64

<figure><img src=".gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Comme

on peut le voir, on obtient donc un hash qui va pouvoir être lu par John directement à ce niveau.

<figure><img src=".gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

\
Rien de très compliqué comme commande, on spécifie simplement notre wordlist, ici on repart avec notre fameux rockyou, et on patiente !

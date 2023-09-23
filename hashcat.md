# 🐈⬛ Hashcat

Pour identifier le type de hash et l'ID dans hascat:

```bash
hashid -m <FILENAME>
```

Exemple de commande:

```bash
hashcat -m 11700 -a 3 chall.txt hack/wordlist/rockyou.txt
```

Pour un hash en sha-1 avec salt tryhackme:

```bash
hashcat -m 110 e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme
```

# 🚡 Feroxbuster

Pour utiliser feroxbuster, cela fonctionne comme gobuster

Pour scanner sur du https qui est bloqué, utiliser le flag -k

Ex:

```bash
feroxbuster -u https://ssa.htb -k -w hack/wordlists/dirbuster/directory-list-2.3-medium.txt -q
```

# 🦧 Mutated Passwords

Pour créer un fichier de mutated passwords:

```bash
hashcat --force passFile -r custom.rule(customRulesFile) --stdout | sort -u > mut_password.list
```

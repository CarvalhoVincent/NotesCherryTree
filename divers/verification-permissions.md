# 👮♂ Vérification permissions

```bash
find / -writable 2>/dev/null
find / -perm -u=s -type f 2>/dev/null
find / -type f -perm -04000 -ls 2>/dev/null
```

puis gtfobins

# 🖼 Fichier caché dans une image

```bash
Binwalk {FILENAME} -e
```

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

&#x20;Un dossier \_cutie.png.extracted a été créé, je me déplace vers ce dernier. Je vois un fichier zip _**8702.zip**_, je vais devoir trouver le mot de passe et pour cela j’utilise _**zip2john**_ :\
_**zip2john 8702.zip > zip.hash**_   création hash compatible pour _**JohnTheRipper**_\
Puis je brute force avec la commande :\
_**john 8702.zip zip.hash**_

# 📦 Libraries

1. **Analyse statique du binaire :** Utilisez des outils tels que `readelf`, `objdump`, ou des outils d'analyse de binaire comme `r2` (Radare2) pour inspecter les informations d'en-tête du binaire. Vous pouvez rechercher les sections `.dynstr`, `.dynsym` et `.dynamic` pour obtenir des informations sur les symboles et les bibliothèques partagées utilisées par le binaire.
2. **Utilisation de ldd :** Vous pouvez exécuter votre programme avec la commande `ldd` en préfixe pour afficher les bibliothèques partagées dont votre programme dépend. Par exemple :

```
ldd /chemin/vers/votre/programme
```

3. **Utilisation de strace :** L'outil `strace` permet de suivre les appels système et les signaux pendant l'exécution d'un programme. Vous pouvez l'utiliser pour suivre les ouvertures de fichiers de bibliothèques partagées. Par exemple :

```
strace -e open /chemin/vers/votre/programme
```

4. **Utilisation de ltrace :** L'outil `ltrace` suit les appels de bibliothèque dynamique effectués par un programme. Il peut être utile pour identifier les fonctions spécifiques appelées à partir des bibliothèques. Par exemple :

```
ltrace /chemin/vers/votre/programme
```

5. **Analyse dynamique :** Vous pouvez utiliser des outils de débogage tels que GDB (GNU Debugger) pour exécuter votre programme et arrêter son exécution à des points d'intérêt. Une fois arrêté, vous pouvez utiliser la commande `info sharedlibrary` pour voir quelles bibliothèques sont chargées à ce stade de l'exécution.

N'oubliez pas que certaines bibliothèques peuvent être chargées dynamiquement pendant l'exécution en fonction des conditions du programme. Par conséquent, il peut être nécessaire de combiner différentes méthodes pour obtenir une image complète des bibliothèques potentiellement appelées.

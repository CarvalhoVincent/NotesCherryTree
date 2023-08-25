# Bloodhound

\


### BloodHound Installation -

1.) `apt-get install bloodhound`    \
2.) `neo4j console` - default credentials -> neo4j:neo4j

### Getting loot w/ SharpHound -&#x20;

```bash
powershell -ep bypass 
//same as with PowerView
```

```bash
. .\Downloads\SharpHound.exe
```

```powershell
Invoke-Bloodhound -CollectionMethod All -Domain CONTROLLER.local -ZipFileName loot.zip
```

<figure><img src="../.gitbook/assets/image (26) (1).png" alt=""><figcaption></figcaption></figure>

\
4.) Transfer the loot.zip folder to your Attacker Machine\
note: you can use scp to transfer the file if you’re using ssh

### Mapping the network w/ BloodHound -

1.) `bloodhound` Run this on your attacker machine not the victim machine\
2.) Sign In using the same credentials you set with Neo4j\


<figure><img src="../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

\
3.) Inside of Bloodhound search for this icon <img src="../.gitbook/assets/image (28) (1).png" alt="" data-size="line"> and import the loot.zip folder\
note: On some versions of BloodHound the import button does not work to get around this simply drag and drop the loot.zip folder into Bloodhound to import the .json files\
4.) To view the graphed network open the menu and select queries this will give you a list of pre-compiled queries to choose from.\


<figure><img src="../.gitbook/assets/image (29) (1).png" alt=""><figcaption></figcaption></figure>

\
The queries can be as simple as find all domain admins -\


<figure><img src="../.gitbook/assets/image (30) (1).png" alt=""><figcaption></figcaption></figure>

\
Or as complicated as shortest path to high value targets -\


<figure><img src="../.gitbook/assets/image (31) (1).png" alt=""><figcaption></figcaption></figure>

\
There are plenty of queries to choose from and enumerate connections inside of the network\

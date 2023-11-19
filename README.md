---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🔥 Watchguard



compatibilités entre les différentes versions, matérielles et logicielles.

T-25 = 5 utilisateurs max



Default Creds

admin:readwrite



{% hint style="info" %}
1 seul compte fonctionne = pas de licence
{% endhint %}





## Nouvelle conf

1. ### Utiliser l’ordonnancement auto
2. ### Logs

_Cocher les deux premières cases du logging_&#x20;

3. ### Applications control actions:

créer une règle permissive pour auditer&#x20;

{% hint style="warning" %}
Pour le proxy, il faut journaliser tout ce qui est autre que allow
{% endhint %}

4.  ### Pas de ANY


5. Pour le DNS, n'autoriser que le contrôleur de domaine à faire les requêtes, et le wifi.



6. ### Pas d'exceptions

***



La règle outgoing permet de voir ce qui à été laissé ouvert et doit disparaître à la fin si tout est bien configuré




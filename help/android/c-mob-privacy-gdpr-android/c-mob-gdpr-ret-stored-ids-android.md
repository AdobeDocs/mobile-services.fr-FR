---
description: Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.
seo-description: Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.
seo-title: Récupération des identifiants stockés
title: Récupération des identifiants stockés
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities stored in the SDK. Vous devez appeler cette méthode **avant** que l’utilisateur ne sélectionne l’option d’exclusion.

Les identités SDK (selon le cas) sont stockées localement et renvoyées dans une chaîne JSON, qui peut contenir :

* Contexte de la société – ID org. IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Marketing Cloud ID
* Codes d’intégration (ADID, ID Push)
* ID de sources de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* ID hérités de Target (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

Voici un exemple de la méthode `ADBMobile getAllIdentifiersAsync` sous Android :

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```

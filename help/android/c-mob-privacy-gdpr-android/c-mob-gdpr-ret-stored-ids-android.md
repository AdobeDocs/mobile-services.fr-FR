---
description: Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.
seo-description: Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.
seo-title: Récupération des identifiants stockés
title: Récupération des identifiants stockés
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 76%

---


# Récupération des identifiants stockés{#retrieving-stored-identifiers}

Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.

>[!IMPORTANT]
>
>La méthode `getAllIdentifiersAsync` récupère les identités stockées dans le SDK. You must call this method **before** the user opts-out.

Les identités du SDK (selon le cas) sont stockées localement et renvoyées dans une chaîne JSON, qui peut contenir :

* Contexte de l’entreprise - ID d’organisation IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Experience Cloud ID
* Codes d’intégration (ADID, Push ID)
* ID de source de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* Identifiants hérités de cible (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

Voici un exemple de la méthode `ADBMobile getAllIdentifiersAsync` sous Android :

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```

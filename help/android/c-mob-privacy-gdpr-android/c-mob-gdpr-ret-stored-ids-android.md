---
description: Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.
title: Récupération des identifiants stockés
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 72%

---

# Récupération des identifiants stockés{#retrieving-stored-identifiers}

Ces informations permettent de récupérer des identités SDK stockées localement à partir de votre application Android et à l’aide de demandes d’accès aux données en vertu du RGPD.

>[!IMPORTANT]
>
>La méthode `getAllIdentifiersAsync` récupère les identités stockées dans le SDK. Vous devez appeler cette méthode **avant** que l’utilisateur se désinscrive.

Les identités du SDK (le cas échéant) sont stockées localement et renvoyées dans une chaîne JSON, qui peut contenir :

* Contexte de l’entreprise - ID d’organisation IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Experience Cloud ID
* Codes d’intégration (ADID, Push ID)
* ID de source de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* Identifiants hérités de Target (TNTID, TNT3rdpartyID)
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

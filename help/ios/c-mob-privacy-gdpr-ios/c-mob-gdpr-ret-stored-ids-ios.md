---
description: Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.
title: Récupération des identifiants stockés
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 67%

---

# Récupération des identifiants stockés{#retrieving-stored-identifiers}

Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.

Pour plus d’informations sur le RGPD, voir [Le RGPD et votre entreprise](https://www.adobe.com/fr/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>La méthode `getAllIdentifiersAsync` récupère les identités qui sont stockées dans les SDK Experience Cloud. Vous devez appeler cette méthode **avant** que l’utilisateur se désinscrive.

Les identités du SDK Experience Cloud (le cas échéant) sont stockées localement et renvoyées dans une chaîne JSON, qui peut contenir :

* Contexte de l’entreprise - ID d’organisation IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Experience Cloud ID
* Codes d’intégration (ADID, Push ID)
* ID de source de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* Identifiants hérités de Target (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

Voici un exemple de la méthode `ADBMobile getAllIdentifiersAsync` dans iOS :

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

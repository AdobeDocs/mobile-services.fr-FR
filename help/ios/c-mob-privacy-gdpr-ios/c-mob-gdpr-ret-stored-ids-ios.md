---
description: Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.
seo-description: Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.
seo-title: Récupération des identifiants stockés
title: Récupération des identifiants stockés
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 69%

---


# Récupération des identifiants stockés{#retrieving-stored-identifiers}

Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.

Pour en savoir plus sur le RGMD, consultez [RGMD et Votre entreprise](https://www.adobe.com/fr/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>La méthode `getAllIdentifiersAsync` récupère les identités qui sont stockées dans les SDK Experience Cloud. You must call this method **before** the user opts-out.

Les identifiants de SDK Experience Cloud (selon le cas) sont stockés localement et renvoyés dans une chaîne JSON, qui peut contenir :

* Contexte de l’entreprise - ID d’organisation IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Experience Cloud ID
* Codes d’intégration (ADID, Push ID)
* ID de source de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* Identifiants hérités de cible (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

Voici un exemple de la méthode `ADBMobile getAllIdentifiersAsync` dans iOS :

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```


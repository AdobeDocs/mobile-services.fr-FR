---
description: Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.
seo-description: Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.
seo-title: Récupération des identifiants stockés
title: Récupération des identifiants stockés
uuid: 4 fb 2 c 166-6700-4 f 8 b-b 60 b -137 b 199 e 0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Consultez ces informations si vous devez récupérer des identités de SDK Experience Cloud stockées localement depuis votre application iOS et conformément aux demandes d’accès aux données en vertu du RGPD.

Pour plus d’informations sur le RGPD, voir [Le RGPD et votre entreprise](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities that are stored in the Experience Cloud SDKs. Vous devez l’invoquer **avant** que l’utilisateur ne se désinscrive.

Les identités de SDK Experience Cloud (le cas échéant) sont stockées localement et renvoyées dans une chaîne JSON, qui peut contenir les éléments suivants :

* Contexte de la société – ID d’organisation IMS
* Identifiants d’utilisateurs
* Experience Cloud ID (MID), précédemment Marketing Cloud ID
* Codes d’intégration (ADID, ID Push)
* ID de sources de données (DPID, DPUUID)
* Analytics ID (AVID, AID, VID et RSID associés)
* ID hérités de Target (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

Voici un exemple de la méthode `ADBMobile getAllIdentifiersAsync` dans iOS :

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```


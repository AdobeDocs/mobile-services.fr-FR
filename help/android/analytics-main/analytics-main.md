---
description: Ces informations vous aident à utiliser le SDK Android avec Adobe Analytics.
keywords: android ; library ; mobile ; sdk
seo-description: Ces informations vous aident à utiliser le SDK Android avec Adobe Analytics.
seo-title: Présentation d'Analytics
solution: Marketing Cloud, Analytics
title: Présentation d'Analytics
topic: Développeur et mise en œuvre
uuid: cc 9 fa 1 d 9-bc 48-4 d 03-854 a-f 7 b 263580 a 91
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Présentation d'Analytics {#analytics}

Les informations de cette section vous aideront à utiliser le SDK Android avec Adobe Analytics.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

>[!IMPORTANT]
>
>Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Génération d'identifiants de suivi Analytics

Dans les SDK, des identifiants sont utilisés pour suivre les utilisateurs, et voici la hiérarchie des identifiants :

1. Identifiant personnalisé de visiteur (VID)
2. Identifiant de suivi des analyses (AID)
3. Identifiant Experience Cloud (MID)

>[!TIP]
>
>L'acronyme correct d'Experience Cloud Identifier est ECID. Même si les SDK utilisent encore MID, qui est l’ancien nom.

L’AID, qui est aussi parfois appelé identifiant de suivi, est généré par le SDK lorsque l’application n’est pas configurée pour utiliser un MID. La valeur persiste entre les lancements et les mises à niveau des applications dans `SharedPreferences`. Si l’utilisateur supprime l’application de son appareil et réinstalle ensuite l’application, ou si le développeur de l’application efface les SharedPreferences, un nouvel identifiant est généré par le SDK. Ce processus se traduit par la création d’un nouvel utilisateur dans le reporting Analytics.

Pour les utilisateurs d’une application qui introduit la prise en charge du service Identity (MID), les valeurs AID existantes sont envoyées avec les accès Analytics, et l’accès Analytics contient un AID et un MID. Pour les nouveaux utilisateurs d’une application prenant en charge le service Identity, les requêtes Analytics ne contiennent qu’un MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
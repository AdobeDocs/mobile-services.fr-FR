---
description: Ces informations vous permettent d’utiliser le SDK iOS avec Adobe Analytics.
seo-description: Ces informations vous permettent d’utiliser le SDK iOS avec Adobe Analytics.
seo-title: Présentation d'Analytics
solution: Marketing Cloud, Analytics
title: Présentation d'Analytics
topic: Développeur et mise en œuvre
uuid: 8 c 7 fb 76 a-be 0 b -4465-8151-ece 7 bad 11 b 55
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Présentation d'Analytics {#analytics}

Les informations de cette section vous aideront à utiliser le SDK ios avec Adobe Analytics.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

## Génération d'identifiants de suivi Analytics

Dans les SDK, des identifiants sont utilisés pour suivre les utilisateurs, et voici la hiérarchie des identifiants :

1. Identifiant personnalisé de visiteur (VID)
2. Identifiant de suivi des analyses (AID)
3. Identifiant Experience Cloud (MID)

>[!TIP]
>
>L'acronyme correct d'Experience Cloud Identifier est ECID. Même si les SDK utilisent encore MID, qui est l’ancien nom.
L’AID, qui est aussi parfois appelé identifiant de suivi, est généré par le SDK lorsque l’application n’est pas configurée pour utiliser un MID. La valeur persiste entre les lancements et les mises à niveau des applications dans `NSUserDefaults`. Si l’utilisateur supprime l’application de son appareil et réinstalle ensuite l’application, ou si le développeur de l’application efface `NSUserDefaults`, un nouvel identifiant est généré par le SDK. Ce processus se traduit par la création d’un nouvel utilisateur dans le reporting Analytics.

Pour les utilisateurs d’une application qui introduit la prise en charge du service Identity (MID), les valeurs AID existantes sont envoyées avec les accès Analytics, et l’accès Analytics contient un AID et un MID. Pour les nouveaux utilisateurs d’une application prenant en charge le service Identity, les requêtes Analytics ne contiennent qu’un MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).

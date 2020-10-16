---
description: Ces informations vous aident à utiliser le SDK Android avec Adobe Analytics.
keywords: android;library;mobile;sdk
seo-description: Ces informations vous aident à utiliser le SDK Android avec Adobe Analytics.
seo-title: Présentation d’Analytics
solution: Experience Cloud,Analytics
title: Présentation d’Analytics
topic: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---


# Présentation d’Analytics {#analytics}

Consultez les informations de cette section lorsque vous utilisez le SDK Android avec Adobe Analytics.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Génération d’identificateurs de suivi des analyses

Dans les SDK, les identifiants sont utilisés pour suivre les utilisateurs et voici leur hiérarchie :

1. Identifiant de visiteur personnalisé (VID)
1. Identifiant de suivi des analyses (AID)
1. Identifiant Experience Cloud (MID)

>[!TIP]
>
>Le bon acronyme pour l’identifiant Experience Cloud est ECID. Même si les SDK utilisent encore MID, qui est l’ancien nom.

L’AID, qui est aussi parfois appelé identifiant de suivi, est généré par le SDK lorsque l’application n’est pas configurée pour utiliser un MID. La valeur persiste entre les lancements et les mises à niveau des applications dans `SharedPreferences`. Si l’utilisateur supprime l’application de son appareil et réinstalle ensuite l’application, ou si le développeur de l’application efface les SharedPreferences, un nouvel identifiant est généré par le SDK. Ce processus génère un nouvel utilisateur dans la création de rapports Analytics.

Pour les utilisateurs d’une application qui introduit la prise en charge du service d’identités (MID), les valeurs AID existantes sont envoyées avec les accès Analytics et l’accès Analytics contient un AID et un MID. Pour les nouveaux utilisateurs dans une application avec prise en charge du service d’identités, les requêtes Analytics ne contiennent qu’un MID. Pour plus d’informations sur l’identification des visiteurs, voir [Identification des visiteurs](https://docs.adobe.com/content/help/fr-FR/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).

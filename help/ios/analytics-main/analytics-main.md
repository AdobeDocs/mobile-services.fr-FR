---
description: Ces informations vous permettent d’utiliser le SDK iOS avec Adobe Analytics.
seo-description: Ces informations vous permettent d’utiliser le SDK iOS avec Adobe Analytics.
seo-title: Présentation d’Analytics
solution: Experience Cloud,Analytics
title: Présentation d’Analytics
topic: Développeur et mise en œuvre
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Présentation d’Analytics {#analytics}

Les informations de cette section vous aident à utiliser le SDK iOS avec Adobe Analytics.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Génération d’identificateurs de suivi des analyses

Dans les SDK, des identifiants sont utilisés pour suivre les utilisateurs, et voici la hiérarchie des identifiants :

1. Identifiant personnalisé de visiteur (VID)
2. Identifiant de suivi des analyses (AID)
3. Identifiant Experience Cloud (MID)

>[!TIP]
>
>Le bon acronyme pour l’identifiant Experience Cloud est ECID. Même si les SDK utilisent encore MID, qui est l’ancien nom. 
L’AID, qui est aussi parfois appelé identifiant de suivi, est généré par le SDK lorsque l’application n’est pas configurée pour utiliser un MID. La valeur persiste entre les lancements et les mises à niveau des applications dans `NSUserDefaults`. Si l’utilisateur supprime l’application de son appareil et réinstalle ensuite l’application, ou si le développeur de l’application efface `NSUserDefaults`, un nouvel identifiant est généré par le SDK. Ce processus se traduit par la création d’un nouvel utilisateur dans le reporting Analytics.

Pour les utilisateurs d’une application qui introduit la prise en charge du service Identity (MID), les valeurs AID existantes sont envoyées avec les accès Analytics, et l’accès Analytics contient un AID et un MID. Pour les nouveaux utilisateurs d’une application prenant en charge le service Identity, les requêtes Analytics ne contiennent qu’un MID. Pour plus d’informations sur l’identification des visiteurs, voir [Identification des visiteurs](https://docs.adobe.com/content/help/fr-FR/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).

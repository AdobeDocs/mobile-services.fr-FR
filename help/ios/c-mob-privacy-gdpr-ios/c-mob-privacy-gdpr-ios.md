---
description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-title: Confidentialité et Règlement général sur la protection des données
title: Confidentialité et Règlement général sur la protection des données
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Confidentialité et Règlement général sur la protection des données {#privacy-and-general-data-protection-regulation}

Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

## New Adobe Experience Platform Mobile SDK Release

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aperçu

Lorsqu’Adobe fournit des logiciels et des services à une entreprise, elle agit en tant qu’entité de traitement des données pour toutes les données personnelles qu’elle traite et stocke dans le cadre de la prestation de ces services. En tant qu’entité de traitement des données, Adobe traite les données personnelles conformément aux autorisations et aux instructions de votre société (par exemple, tel qu’énoncé dans votre accord avec Adobe).

En tant que contrôleur de données, vous pouvez utiliser les SDK Adobe Mobile Services pour prendre en charge les demandes de récupération et de suppression conformes au RGPD depuis vos applications mobiles.

Pour les parties du SDK Adobe Mobile de vos applications mobiles, vous pouvez utiliser les méthodes et paramètres suivants :

* Pour récupérer les données des SDK et envoyer ces données à vos serveurs, utilisez la méthode `getAllIdentifiersAsync`.

   For more information, see Retrieving Stored Identifiers.[](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)

* Pour définir votre état de souscription et vous aider en cas de demande de suppression de données en vertu du RGPD, utilisez les paramètres suivants :

   * `privacyDefault`
   * `setPrivacyStatus`
   For more information, see Setting the User's Opt Status.[](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)

## Informations supplémentaires {#section_7C7124C50D85469C8C8714533FB1A37D}

* Pour plus d’informations sur le RGPD, voir [Le RGPD et votre entreprise](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Pour consulter la documentation sur l’API relative au RGPD, voir la section traitant de l’[API relative au règlement général sur la protection des données](https://adobe.io/apis/cloudplatform/gdpr.html) (en anglais).


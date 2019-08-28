---
description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-title: Confidentialité et Règlement général sur la protection des données
title: Confidentialité et Règlement général sur la protection des données
uuid: 69 bb 82 de -1993-440 c-a 1 b 0-8 d 37919 b 48 b 6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Confidentialité et Règlement général sur la protection des données {#privacy-and-general-data-protection-regulation}

Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Lorsqu’Adobe fournit des logiciels et des services à une entreprise, elle agit en tant qu’entité de traitement des données pour toutes les données personnelles qu’elle traite et stocke dans le cadre de la prestation de ces services. En tant qu’entité de traitement des données, Adobe traite les données personnelles conformément aux autorisations et aux instructions de votre société (par exemple, tel qu’énoncé dans votre accord avec Adobe).

En tant que contrôleur de données, vous pouvez utiliser les SDK Adobe Mobile Services pour prendre en charge les demandes de récupération et de suppression conformes au RGPD depuis vos applications mobiles.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


Pour les parties du SDK Adobe Mobile de vos applications mobiles, vous pouvez utiliser les méthodes et paramètres suivants :

* Pour récupérer les données des SDK et envoyer ces données à vos serveurs, utilisez la méthode `getAllIdentifiersAsync`.

   Pour plus d'informations, voir [Récupération des identifiants stockés](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Pour définir votre état de souscription et vous aider en cas de demande de suppression de données en vertu du RGPD, utilisez les paramètres suivants :

   * `privacyDefault`
   * `setPrivacyStatus`
   Pour plus d'informations, voir [Définition de l'état d'exclusion de l'utilisateur](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Informations supplémentaires {#section_7C7124C50D85469C8C8714533FB1A37D}

* Pour plus d’informations sur le RGPD, voir [Le RGPD et votre entreprise](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Pour consulter la documentation sur l’API relative au RGPD, voir la section traitant de l’[API relative au règlement général sur la protection des données](https://adobe.io/apis/cloudplatform/gdpr.html) (en anglais).


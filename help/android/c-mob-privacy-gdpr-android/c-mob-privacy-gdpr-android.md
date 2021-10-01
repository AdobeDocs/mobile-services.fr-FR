---
description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
title: Présentation du Règlement général sur la protection des données
uuid: 56d6f155-efec-4b3f-a972-a63155729167
exl-id: 57696f2e-87f4-4f72-bec2-80c7192576f9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 76%

---

# Présentation du Règlement général sur la protection des données {#privacy-and-general-data-protection-regulation}

Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aperçu

>[!IMPORTANT]
>
>Le RGPD est pris en charge **uniquement** dans la version 4.16.0 ou ultérieure du SDK Mobile.

Lorsqu’Adobe fournit des logiciels et des services à une entreprise, elle agit en tant qu’entité de traitement des données pour toutes les données personnelles qu’elle traite et stocke dans le cadre de la prestation de ces services. En tant qu’entité de traitement des données, Adobe traite les données personnelles conformément aux autorisations et aux instructions de votre société (par exemple, tel que défini dans votre accord avec votre Adobe).

En tant que contrôleur des données, vous pouvez utiliser les SDK Adobe Mobile Services pour prendre en charge les demandes de récupération et de suppression en vertu du RGPD de vos applications mobiles.

Pour les parties du SDK Adobe Mobile de vos applications mobiles, vous pouvez utiliser les méthodes et paramètres suivants :

* Pour récupérer les données des SDK et envoyer ces données à vos serveurs, utilisez la méthode `getAllIdentifiersAsync`.

   Pour plus d’informations, voir [Récupération des identifiants stockés](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Pour définir votre état de souscription et vous aider en cas de demande de suppression de données en vertu du RGPD, utilisez les paramètres suivants :

   * `privacyDefault`
   * `setPrivacyStatus`
   Pour plus d’informations, voir [Définition de l’état d’exclusion de l’utilisateur](/help/android/c-mob-privacy-gdpr-android/privacy.md).

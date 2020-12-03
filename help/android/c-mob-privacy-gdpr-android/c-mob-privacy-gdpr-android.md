---
description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-description: Les SDK Experience Cloud Mobile contiennent des API conformes au règlement général sur la protection des données (RGPD) destinées aux contrôleurs qui autorisent les utilisateurs à récupérer des identités stockées localement et à définir des indicateurs d’état de souscription pour la collecte et la transmission de données.
seo-title: Présentation du Règlement général sur la protection des données
title: Présentation du Règlement général sur la protection des données
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 78%

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

Lorsque l&#39;Adobe fournit des logiciels et des services à une entreprise, l&#39;Adobe agit comme un processeur de données pour toutes les données personnelles qu&#39;il traite et stocke dans le cadre de la prestation de ces services. En tant que traitement de données, l’Adobe traite les données à caractère personnel conformément à l’autorisation et aux instructions de votre société (par exemple, conformément à votre accord avec l’Adobe).

En tant que contrôleur de données, vous pouvez utiliser les Adobes Mobile Services SDK pour prendre en charge la récupération et la suppression de requêtes GDPR de vos applications mobiles.

Pour les parties du SDK Adobe Mobile de vos applications mobiles, vous pouvez utiliser les méthodes et paramètres suivants :

* Pour récupérer les données des SDK et envoyer ces données à vos serveurs, utilisez la méthode `getAllIdentifiersAsync`.

   Pour plus d’informations, voir [Récupération des identifiants stockés](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Pour définir votre état de souscription et vous aider en cas de demande de suppression de données en vertu du RGPD, utilisez les paramètres suivants :

   * `privacyDefault`
   * `setPrivacyStatus`
   Pour plus d’informations, voir [Définition de l’état d’exclusion de l’utilisateur](/help/android/c-mob-privacy-gdpr-android/privacy.md).
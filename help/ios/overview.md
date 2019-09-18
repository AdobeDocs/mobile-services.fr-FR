---
description: Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.
seo-description: Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.
seo-title: SDK iOS 4.x pour solutions Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK iOS 4.x pour solutions Experience Cloud
topic: Développeur et mise en œuvre
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 1070450065776fdb7d13e9b21ce62ceeee55b80e

---


# SDK iOS 4.x pour solutions Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.

>[!IMPORTANT]
>
>Le SKU du module complémentaire de marketing mobile Adobe Analytics est nécessaire pour permettre aux services mobiles d’accéder aux fonctionnalités d’acquisition mobile, de liaison profonde, de géolocalisation et de messagerie mobile. Pour plus d’informations, contactez votre Adobe CSM.

>[!IMPORTANT]
>
>Le SDK mobile d’Adobe Experience Platform prend désormais en charge [iOS 13 et Xcode 11][https://developer.apple.com/ios/]. Pour garantir une compatibilité transparente, utilisez les [dernières versions de l’extension](https://app.gitbook.com/@aep-sdks/s/docs/resources/frequently-asked-questions/current-sdk-versions)SDK Experience Platform Mobile.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Informations à retenir :

* iOS 5 ou version ultérieure compatible

   Pour iOS 11 ou version ultérieure, vous **devez** disposer de la version 4.13.8 ou ultérieure du SDK.

* Dans la version 4.2 de ce SDK ou une version ultérieure, tous les accès sont désormais envoyés par HTTP POST.

   Cela n’a aucun impact sur les données collectées ou rapportées, mais vous devez utiliser un analyseur de paquets qui prend en charge l’inspection des données POST pour afficher les accès.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Documentation utilisateur Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services offre une nouvelle interface utilisateur qui réunit les fonctionnalités de marketing mobile pour les applications mobiles issues d’Adobe Experience Cloud. Au départ, le service Mobile intègre de manière transparente les fonctionnalités d’analyse et de ciblage des applications issues des solutions Adobe Analytics, Adobe Audience Manager et Adobe Target, ainsi que du service d’identité de la plate-forme Adobe Experience Platform.

Pour en savoir plus sur l’interface utilisateur de Mobile Services et lire la documentation utilisateur, reportez-vous à [Adobe Mobile Services](/help/using/home.md).

## Utilisation de Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Depuis le 1er mai 2017, plus aucune amélioration n’y est apportée et aucune assistance d’ingénierie supplémentaire ou assistance Adobe Expert Care n’est fournie.

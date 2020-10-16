---
description: Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.
seo-description: Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.
seo-title: SDK iOS 4.x pour solutions Experience Cloud
solution: Experience Cloud,Analytics
title: SDK iOS 4.x pour solutions Experience Cloud
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 100%

---


# SDK iOS 4.x pour solutions Experience Cloud {#ios-sdk-x-for-experience-cloud-solutions}

Le SDK iOS 4.x pour solutions Experience Cloud permet de mesurer les applications iPhone et iPad Apple natives, de diffuser du contenu ciblé dans vos applications, ainsi que d’exploiter et de collecter des données d’audience grâce à Audience Manager.

>[!IMPORTANT]
>
>Le SKU du module complémentaire de marketing mobile Adobe Analytics est nécessaire pour permettre aux Mobile Services d’accéder aux fonctionnalités d’acquisition mobile, de lien profond, de géolocalisation et de messagerie mobile. Pour en savoir plus, contactez votre CSM Adobe.

>[!IMPORTANT]
>
>Le SDK iOS 4.x pour solutions Experience Cloud prend désormais en charge [iOS 13 et Xcode 11](https://developer.apple.com/ios/). Pour garantir une compatibilité fluide, utilisez les dernières versions des SDK iOS 4.x. Pour plus d’informations sur la dernière version, voir les [notes de mise à jour](/help/ios/rel-notes.md).

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Informations à retenir :

* iOS 8 ou version ultérieure compatible.

   Pour iOS 11 ou version ultérieure, vous **devez** disposer du SDK version 4.13.8 ou ultérieure.

* Dans la version 4.2 de ce SDK ou une version ultérieure, tous les accès sont désormais envoyés par HTTP POST.

   Cela n’a aucun impact sur les données collectées ou reprises dans les rapports, mais vous devez utiliser un analyseur de paquets qui prend en charge l’inspection des données POST pour afficher les accès.

* Si vous procédez à une mise à niveau depuis une version précédente (2.x ou 3.x), consultez le [Guide de la migration 4.x](/help/ios/getting-started/migration-v3.md).

## Documentation utilisateur Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services offre une nouvelle interface utilisateur qui réunit les fonctionnalités de marketing mobile pour les applications mobiles issues d’Adobe Experience Cloud. Adobe Mobile offre une intégration en toute transparence des fonctionnalités d’analyse et de ciblage des applications issues des solutions Adobe Analytics, Adobe Audience Manager et Adobe Target, ainsi que du service d’identification Adobe Experience Platform.

Pour en savoir plus sur l’interface utilisateur de Mobile Services et lire la documentation utilisateur, reportez-vous à [Adobe Mobile Services](/help/using/home.md).

## Utilisation de Bloodhound

>[!IMPORTANT]
>
>Depuis le **30 avril 2017**, Adobe Bloodhound fait l’objet d’une élimination progressive. Depuis le 1er mai 2017, plus aucune amélioration n’y est apportée et aucune assistance d’ingénierie supplémentaire ou assistance Adobe Expert Care n’est fournie.

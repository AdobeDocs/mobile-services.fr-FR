---
description: Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.
keywords: android;library;mobile;sdk
seo-description: Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.
seo-title: SDK Android 4.x pour solutions Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK Android 4.x pour solutions Experience Cloud
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '447'
ht-degree: 100%

---


# SDK Android 4.x pour solutions Experience Cloud {#android-sdk-x-for-experience-cloud-solutions}

Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Le SKU du module complémentaire de marketing mobile Adobe Analytics est nécessaire pour permettre aux Mobile Services d’accéder aux fonctionnalités d’acquisition mobile, de lien profond, de géolocalisation et de messagerie mobile. Pour en savoir plus, contactez votre CSM Adobe.

>[!IMPORTANT]
>
>Bien que vous puissiez configurer des fonctionnalités dans l’interface utilisateur, elles ne fonctionneront pas tant que vous n’aurez pas téléchargé le fichier de configuration généré et ajouté ce fichier au SDK. Pour plus d’informations sur le téléchargement et la configuration des SDK, voir [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

Les SDK prennent en charge les versions suivantes d’Android :

* La version 4.6.0 ou antérieure prend en charge Android 2.2 (API 8) - Android 5.1.1 (API 22).
* La version 4.6.1 ou ultérieure prend en charge Android 2.3 (API 9) ou version ultérieure.

Informations à retenir :

* Dans la version 4.2 ou ultérieure, tous les accès sont désormais envoyés par HTTP POST.

   Cela n’a aucun impact sur les données collectées ou reprises dans les rapports, mais vous devez utiliser un analyseur de paquets qui prend en charge l’inspection des données POST pour afficher les accès.

* Si vous procédez à une mise à niveau depuis une version précédente, consultez le [Guide de la migration 4.x](/help/android/getting-started/migration-v3.md).

## Documentation utilisateur Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fournit une interface utilisateur qui réunit les fonctionnalités de marketing pour les applications mobiles issues d’Adobe Experience Cloud. Pour en savoir plus sur l’interface utilisateur et lire la documentation utilisateur, reportez-vous à [Adobe Mobile Services](https://docs.adobe.com/content/help/fr-FR/mobile-services/using/home.html).

## Notes de mise à jour {#section_F8181DC052D44DD2A99AB40A41F6792C}

Pour consulter les informations les plus récentes sur les versions d’Experience Cloud, voir [Notes de mise à jour d’Experience Cloud](https://docs.adobe.com/content/help/fr-FR/release-notes/experience-cloud/current.html).

## Utilisation de Bloodhound

>[!IMPORTANT]
>
>Depuis le **30 avril 2017**, Adobe Bloodhound fait l’objet d’une élimination progressive. Depuis le 1er mai 2017, plus aucune amélioration n’y est apportée et aucune assistance d’ingénierie supplémentaire ou assistance Adobe Expert Care n’est fournie.

---
description: Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.
keywords: android;library;mobile;sdk
seo-description: Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.
seo-title: SDK Android 4.x pour solutions Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK Android 4.x pour solutions Experience Cloud
topic: Développeur et mise en œuvre
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Le SDK Android 4.x pour solutions Experience Cloud permet de mesurer les applications Android natives, de fournir un contenu ciblé à l’application et d’utiliser et collecter les données d’audience à l’aide de la gestion de l’audience.

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Le SKU du module complémentaire de marketing mobile Adobe Analytics est nécessaire pour permettre aux services mobiles d’accéder aux fonctionnalités d’acquisition mobile, de liaison profonde, de géolocalisation et de messagerie mobile. Pour plus d’informations, contactez votre Adobe CSM.

>[!IMPORTANT]
>
>Bien que vous puissiez configurer des fonctionnalités dans l’interface utilisateur, ces fonctionnalités ne fonctionneront pas tant que vous n’aurez pas téléchargé le fichier de configuration généré et ajouté ce fichier au SDK. Pour plus d’informations sur le téléchargement et la configuration des SDK, voir Mise en oeuvre [principale et cycle de vie](/help/android/getting-started/dev-qs.md).

Les SDK prennent en charge les versions suivantes d’Android :

* La version 4.6.0 ou version antérieure prend en charge Android 2.2 (API 8) à Android 5.1.1 (API 22).
* La version 4.6.1 ou version ultérieure prend en charge Android 2.3 (API 9) ou version ultérieure.

Informations à retenir :

* Dans les versions 4.2 et ultérieures, tous les accès sont désormais envoyés à l’aide de HTTP POST.

   Cela n’a aucun impact sur les données collectées ou rapportées, mais vous devez utiliser un analyseur de paquets qui prend en charge l’inspection des données POST pour afficher les accès.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fournit une interface utilisateur qui réunit les fonctionnalités de marketing pour les applications mobiles issues d’Adobe Experience Cloud. Pour en savoir plus sur l’interface utilisateur et lire la documentation utilisateur, voir [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/).

## Notes de mise à jour {#section_F8181DC052D44DD2A99AB40A41F6792C}

Pour consulter les informations les plus récentes sur les versions d’Experience Cloud, voir [Notes de mise à jour d’Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

## Utilisation de Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Depuis le 1er mai 2017, plus aucune amélioration n’y est apportée et aucune assistance d’ingénierie supplémentaire ou assistance Adobe Expert Care n’est fournie.

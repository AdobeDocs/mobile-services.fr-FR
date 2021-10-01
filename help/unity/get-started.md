---
description: Ce module externe permet d’envoyer des appels Adobe Analytics depuis les applications Unity.
keywords: Unity
solution: Experience Cloud
title: Module externe Unity pour SDK iOS et Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
exl-id: fdb012d0-64f5-4c63-96d7-508fef01041f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 100%

---

# Module externe Unity pour SDK iOS et Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Ce module externe permet d’envoyer des appels Adobe Analytics depuis les applications Unity.

Dernière mise à jour : **10 mars 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Prise en main {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Téléchargez le fichier ADBMobile.unitypackage sur GitHub.

Voici le contenu du fichier `ADBMobile.unitypackage` :

* Ressources (racine)

   * ADBMobile

   * Modules externes

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * ressources

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**Dossiers facultatifs** : le dossier *Demo* contient des scènes Unity et un exemple de code.

## Importation du module externe ADBMobile dans un projet Unity  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Ouvrez le projet Unity.
1. Double-cliquez sur **[!UICONTROL ADBMobile.unitypackage]**.
1. Sélectionnez les dossiers à importer.

---
description: Ce module externe permet d’envoyer des appels Adobe Analytics depuis les applications Unity.
keywords: Unity
seo-description: Ce module externe permet d’envoyer des appels Adobe Analytics depuis les applications Unity.
seo-title: Module externe Unity pour SDK iOS et Android 4.x
solution: Marketing Cloud,Développeur
title: Module externe Unity pour SDK iOS et Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Module externe Unity pour SDK iOS et Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Ce module externe permet d’envoyer des appels Adobe Analytics depuis les applications Unity.

Dernière mise à jour : **20 octobre 2016**

## Prise en main {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Téléchargez le fichier [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) depuis GitHub ou Developer Connection.

Voici le contenu du `ADBMobile.unitypackage` fichier :

* Ressources (racine)

   * ADBMobile

      * Démonstration

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
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



Dossiers facultatifs : le dossier Démo contient des scènes et un exemple de code Unity pour chacune des langues de script prises en charge.

## Importation du module externe ADBMobile dans un projet Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Ouvrez le projet Unity.
1. Double-cliquez sur **[!UICONTROL ADBMobile.unitypackage]**.
1. Sélectionnez les dossiers à importer.


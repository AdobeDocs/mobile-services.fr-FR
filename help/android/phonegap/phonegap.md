---
description: Ce module permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap.
keywords: android;library;mobile;sdk
seo-description: Ce module permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap.
seo-title: Présentation du module PhoneGap
solution: Marketing Cloud,Analytics
title: Présentation du module PhoneGap
topic: Développeur et mise en œuvre
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Présentation du module PhoneGap {#phonegap-plug-in}

Ce module permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap. Pour créer un projet PhoneGap, voir [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Installation du module externe à l’aide de npm {#section_43229E57C16944C0B51531CB92089189}

Exécutez la commande suivante :

```java
cordova plugin add adobe-mobile-services
```

## Installation manuelle du module externe {#section_EA1FD59C484D44878AB509954DEE6037}

## Inclusion du module

1. Faites glisser le `ADBMobile_PhoneGap.java` fichier vers votre `src` dossier.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. Faites glisser le `ADB_Helper.js` fichier dans le dossier contenant le `index.html` fichier

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Par exemple, si votre module est nommé `com.example.phonegaptest`, la valeur de `android-package` serait la suivante :

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Inclure la bibliothèque AppMeasurement

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. Faites glisser le `adobeMobileLibrary.jar` fichier vers votre `src` dossier.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. Selon les exigences de votre projet, saisissez le nom, le niveau et l’emplacement de la bibliothèque.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. Confirmez que vous avez sélectionné l’application racine et **non** une application dans une application.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

## Add app permissions

La bibliothèque AppMeasurement nécessite les autorisations suivantes pour envoyer des données et enregistrer les appels de suivi hors ligne :

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Pour ajouter ces autorisations, ajoutez les lignes suivantes au fichier `AndroidManifest.xml`, situé dans le répertoire du projet d’application :

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Pour activer la messagerie intégrée (in-app), procédez comme suit :

Mettez à jour AndroidManifest.xml pour déclarer l’activité Plein écran et activer le gestionnaire de notifications de messages :

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Si vous sélectionnez la disposition modale lorsque vous créez un message dans Adobe Mobile Services, sélectionnez l’un des thèmes suivants :

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Par exemple :

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```


---
description: Ce module externe permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap.
keywords: android;library;mobile;sdk
seo-description: Ce module externe permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap.
seo-title: Présentation du module externe PhoneGap
solution: Experience Cloud,Analytics
title: Présentation du module externe PhoneGap
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 97%

---

# Présentation du module externe PhoneGap {#phonegap-plug-in}

Ce module externe permet d’envoyer des appels AppMeasurement pour Android à partir de votre projet PhoneGap. Pour créer un projet PhoneGap, voir [PhoneGap](https://helpx.adobe.com/fr/experience-manager/6-4/mobile/using/phonegap.html).

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Installation du module externe à l’aide de npm {#section_43229E57C16944C0B51531CB92089189}

Exécutez la commande suivante :

```java
cordova plugin add adobe-mobile-services
```

## Installation manuelle du module externe  {#section_EA1FD59C484D44878AB509954DEE6037}

## Inclusion du module externe

1. Faites glisser le fichier `ADBMobile_PhoneGap.java` vers votre dossier `src`.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. Faites glisser le fichier `ADB_Helper.js` dans le dossier contenant le fichier `index.html`

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. Dans le dossier `res/xml`, ouvrez le fichier `config.xml` et enregistrez un nouveau module externe en ajoutant ce qui suit :

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Par exemple, si votre module est nommé `com.example.phonegaptest`, la valeur de `android-package` serait la suivante :

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Inclusion de la bibliothèque AppMeasurement

1. Pour télécharger la bibliothèque AppMeasurement, voir [Obtention du SDK](/help/android/getting-started/dev-qs.md).
1. Faites glisser le fichier `adobeMobileLibrary.jar` vers votre dossier `src`.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

1. Cliquez avec le bouton droit sur le fichier `adobeMobileLibrary.jar` et sélectionnez **[!UICONTROL Ajouter en tant que bibliothèque]**.
1. Selon les exigences de votre projet, saisissez le nom, le niveau et l’emplacement de la bibliothèque.
1. Faites glisser le fichier `ADBMobileConfig.json` vers le dossier `assets` de la racine de l’application.
1. Confirmez que vous avez sélectionné l’application racine et **non** une application dans une application.

   Pour déplacer ce fichier, cliquez sur **[!UICONTROL OK]**.

## Ajout des autorisations des applications

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

## Mise en œuvre d’un suivi personnalisé {#section_FD102B3CDAA4492FB04E56BF17E28663}

Dans les fichiers `html` pour lesquels vous voulez utiliser le suivi, ajoutez le code ci-après à la balise `<head>` :

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

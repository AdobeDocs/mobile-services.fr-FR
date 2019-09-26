---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. When a user downloads and runs an app from the App store after clicking on the generated link, the SDK automatically collects and sends the acquisition data to Adobe Mobile services.
keywords: android;library;mobile;sdk
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition aux services Adobe Mobile.
seo-title: Acquisition des applications mobiles
solution: Marketing Cloud,Analytics
title: Acquisition des applications mobiles
topic: Développeur et mise en œuvre
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Mobile app acquisition {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition aux services Adobe Mobile.

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Pour utiliser Acquisition, vous **devez** disposer de la version 4.1 ou supérieure du SDK.

Les liens d’acquisition doivent être créés dans Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**Dans le SDK versions 4.13.1 et supérieures** :

Si vous ne pouvez pas utiliser les liens d’acquisition créés dans Adobe Mobile Services, les données d’acquisition peuvent tout de même être collectées et envoyées par le SDK à l’aide de Google Play Acquisition.

Pour collecter des données d’acquisition depuis une campagne Google Play Acquisition standard, procédez comme suit :

* Utilisez la méthode d’acquisition de la boutique Google Play standard.

   Vous pouvez utiliser les données d’acquisition personnalisées avec les paires clé-valeur Google Play Acquisition standard.

* Lorsque l’utilisateur télécharge et exécute une application résultant d’une acquisition de la boutique Google Play, les données provenant du référent sont collectées et envoyées à Adobe Mobile Services.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      For more information, see Configuration Methods.[](/help/android/configuration/methods.md)

   * The  or the  event type are used.`MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL``MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`

   * Les clés personnalisées qui faisaient partie des données d’acquisition de Google Play sont placées dans un espace de noms avec « `a.acquisition.custom.` ».

Si vous utilisez les liens d’acquisition créés dans Adobe Mobile Services, ajoutez des données personnalisées au lien d’acquisition en procédant comme suit :

1. Attribuez le préfixe « `adb` » à une variable d’acquisition.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. The  or the  event type will be used.`MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL``MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`

1. The custom data keys are prefixed with "`a.acquisition.custom.`"

>[!TIP]
>
>Si vous envoyez des données à plusieurs suites de rapports, utilisez les données d’acquisition de l’application associée à la première suite de rapports dans votre liste d’identifiants de suites de rapports.

Les mises à jour de cette section permettent au SDK d’envoyer les données d’acquisition depuis un lien d’acquisition.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Add the library [to your project and implement lifecycle.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Implémentez le `BroadcastReceiver` pour le référent :

   ```java
   package com.your.package.name;  // replace with your app package name 
   
   import android.content.BroadcastReceiver; 
   import android.content.Context; 
   import android.content.Intent; 
   
   public class GPBroadcastReceiver extends BroadcastReceiver { 
     @Override 
     public void onReceive(Context c, Intent i) { 
      com.adobe.mobile.Analytics.processReferrer(c, i); 
     } 
   }
   ```

1. Mettez à jour `AndroidManifest.xml` pour activer le `BroadcastReceiver` créé à l’étape précédente :

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
    <intent-filter> 
     <action android:name="com.android.vending.INSTALL_REFERRER" /> 
    </intent-filter> 
   </receiver>
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   > Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d’acquisition (serveur d’acquisition et appid) provenant de l’application associée à la première suite de rapports de la liste d’identifiants des suites de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Une fois que ces paramètres sont activés, après le lancement initial de l’application, les données d’acquisition sont envoyées automatiquement avec l’appel initial du cycle de vie.

>[!CAUTION]
>
>`referrerTimeout`  Pour activer l’acquisition d’applications,  doit être défini sur une valeur supérieure à 0.

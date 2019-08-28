---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu'un utilisateur télécharge et exécute une application à partir de l'App Store après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d'acquisition aux services Adobe Mobile.
keywords: android ; library ; mobile ; sdk
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu'un utilisateur télécharge et exécute une application à partir de l'App Store après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d'acquisition aux services Adobe Mobile.
seo-title: Acquisition des applications mobiles
solution: Marketing Cloud, Analytics
title: Acquisition des applications mobiles
topic: Développeur et mise en œuvre
uuid: 4 d 32 eae 9-e 856-4 e 40-8 a 29-2 b 5 bccd 106 e 0
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile app acquisition {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu'un utilisateur télécharge et exécute une application à partir de l'App Store après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d'acquisition aux services Adobe Mobile.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using Acquisition and Marketing Links with the Experience Cloud SDKs, see [Acquisition and Marketing Links](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#acquisition-and-marketing-links).

>[!IMPORTANT]
>
>Pour utiliser Acquisition, vous **devez** disposer de la version 4.1 ou supérieure du SDK.

Les liens d’acquisition doivent être créés dans Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**Dans le SDK versions 4.13.1 et supérieures** :

Si vous ne pouvez pas utiliser les liens d’acquisition créés dans Adobe Mobile Services, les données d’acquisition peuvent tout de même être collectées et envoyées par le SDK à l’aide de Google Play Acquisition.

Pour collecter des données d’acquisition depuis une campagne Google Play Acquisition standard, procédez comme suit :

* Utilisez la méthode d’acquisition de la boutique Google Play standard.

   Vous pouvez utiliser les données d’acquisition personnalisées avec les paires clé-valeur Google Play Acquisition standard.

* Lorsque l’utilisateur télécharge et exécute une application résultant d’une acquisition de la boutique Google Play, les données provenant du référent sont collectées et envoyées à Adobe Mobile Services.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      Pour plus d'informations, voir [Méthodes de configuration](/help/android/configuration/methods.md).

   * Le type `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` d'événement ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` d'événement est utilisé.

   * Les clés personnalisées qui faisaient partie des données d’acquisition de Google Play sont placées dans un espace de noms avec « `a.acquisition.custom.` ».

Si vous utilisez les liens d’acquisition créés dans Adobe Mobile Services, ajoutez des données personnalisées au lien d’acquisition en procédant comme suit :

1. Attribuez le préfixe « `adb` » à une variable d’acquisition.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. Le `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` type d `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 'événement est utilisé.

1. Les clés de données personnalisées sont préfixés avec`a.acquisition.custom.`

>[!TIP]
>
>Si vous envoyez des données à plusieurs suites de rapports, utilisez les données d'acquisition de l'application associée à la première suite de rapports dans la liste des ID de suite de rapports.

Les mises à jour de cette section permettent au SDK d’envoyer les données d’acquisition depuis un lien d’acquisition.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Ajoutez la bibliothèque [à votre projet et implémentez le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier Config à votre projet intellij IDEA ou Eclipse* dans [l'implémentation principale et le cycle de vie](/help/android/getting-started/dev-qs.md).

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
   >Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d'acquisition (serveur d'acquisition et appid) de l'application associée à la première suite de rapports dans la liste des ID de suite de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Une fois que ces paramètres sont activés, après le lancement initial de l’application, les données d’acquisition sont envoyées automatiquement avec l’appel initial du cycle de vie.

>[!CAUTION]
>
>`referrerTimeout` doit être définie sur une valeur supérieure à 0 pour activer l'acquisition de l'application.

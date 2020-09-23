---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de la boutique d’applications après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
keywords: android;library;mobile;sdk
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de la boutique d’applications après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-title: Acquisition des applications mobiles
solution: Experience Cloud,Analytics
title: Acquisition des applications mobiles
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 100%

---


# Acquisition des applications mobiles {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de la boutique d’applications après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Pour utiliser Acquisition, vous **devez** disposer de la version 4.1 ou supérieure du SDK.

Les liens Acquisition doivent être créés dans Adobe Mobile Services. Pour en savoir plus, consultez la rubrique [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**Dans le SDK versions 4.18.0 et supérieures** :

À partir du 1er mars 2020, Google abandonne le mécanisme de diffusion de l’intention install_referrer. Pour plus d’informations, consultez [Still Using InstallBroadcast? Switch to the Play Referrer API by March 1, 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) (article en anglais). Pour continuer à collecter des informations sur les référents d’installation à partir de la boutique Google Play, mettez à jour votre application afin d’utiliser le SDK version 4.18.0 ou ultérieure.

Avec cet abandon, au lieu de créer un `BroadcastReceiver`, vous devez collecter l’URL du référent d’installation à partir d’une nouvelle API Google et transmettre l’URL qui en résulte au SDK.

1. Ajoutez le package Google Play Install Referrer aux dépendances de votre fichier Gradle :

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Pour récupérer l’URL du référent à partir de l’API du référent d’installation, suivez la procédure décrite dans [Getting the install referrer](https://developer.android.com/google/play/installreferrer/library#install-referrer) (Obtention du référent d’installation).

1. Transmettez l’URL du référent au SDK :

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Pour éviter les appels d’API inutiles dans votre application, Google vous recommande de n’appeler l’API qu’une seule fois immédiatement après l’installation.

Pour déterminer la meilleure façon d’utiliser les API de référents d’installation de Google Play dans votre application, consultez la documentation Google. Voici un exemple d’utilisation du SDK Adobe avec les API de référents d’installation de Google Play :

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**Dans le SDK versions 4.13.1 et supérieures** :

Si vous ne pouvez pas utiliser les liens d’acquisition créés dans Adobe Mobile Services, les données d’acquisition peuvent tout de même être collectées et envoyées par le SDK à l’aide de Google Play Acquisition.

Pour collecter des données d’acquisition depuis une campagne Google Play Acquisition standard, procédez comme suit :

* Utilisez la méthode d’acquisition de la boutique Google Play standard.

   Vous pouvez utiliser les données d’acquisition personnalisées avec les paires clé-valeur Google Play Acquisition standard.

* Lorsque l’utilisateur télécharge et exécute une application résultant d’une acquisition de la boutique Google Play, les données provenant du référent sont collectées et envoyées à Adobe Mobile Services.

   * Les données sont stockées et disponibles dans l’instance `AdobeDataCallback` enregistrée antérieurement avec le SDK.

      Pour plus d’informations, voir [Méthodes de configuration](/help/android/configuration/methods.md).

   * Le type d’événement `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` est utilisé.

   * Les clés personnalisées qui faisaient partie des données d’acquisition de Google Play sont placées dans un espace de noms avec « `a.acquisition.custom.` ».

Si vous utilisez les liens d’acquisition créés dans Adobe Mobile Services, ajoutez des données personnalisées au lien d’acquisition en procédant comme suit :

1. Attribuez le préfixe « `adb` » à une variable d’acquisition.

   Lorsque le SDK reçoit les données d’acquisition d’Adobe Mobile Services lors du premier lancement, les données sont stockées et disponibles dans l’instance `AdobeDataCallback` enregistrée auparavant avec le SDK. Pour plus d’informations, voir [Méthodes de configuration](/help/android/configuration/methods.md).

1. Le type d’événement `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` sera utilisé.

1. Les clés de données personnalisées comportent le préfixe « `a.acquisition.custom.` ».

>[!TIP]
>
>Si vous envoyez des données à plusieurs suites de rapports, utilisez les données d’acquisition provenant de l’application associée à la première suite de rapports de la liste d’identifiants des suites de rapports.

Les mises à jour de cette section permettent au SDK d’envoyer les données d’acquisition depuis un lien d’acquisition.

## Suivi des acquisitions mobiles {#section_CEA30C652AC8470784B8054E299B80FA}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration au projet IntelliJ IDEA ou Eclipse* dans [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

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

1. Vérifiez que le fichier `ADBMobileConfig.json` comporte les paramètres d’acquisition requis :

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
   >Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d’acquisition (serveur d’acquisition et appid) provenant de l’application associée à la première suite de rapports de la liste d’identifiants des suites de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. Pour obtenir plus d’informations sur le mode de téléchargement d’un fichier `ADBMobileConfig.json` personnalisé avec les paramètres `acquisition` préconfigurés, voir [Avant de démarrer](/help/android/getting-started/requirements.md).

Une fois que ces paramètres sont activés, après le lancement initial de l’application, les données d’acquisition sont envoyées automatiquement avec l’appel initial du cycle de vie.

>[!CAUTION]
>
>Pour activer l’acquisition d’applications, `referrerTimeout` doit être défini sur une valeur supérieure à 0.

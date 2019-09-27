---
description: Classes et méthodes fournies par la bibliothèque BlackBerry.
seo-description: Classes et méthodes fournies par la bibliothèque BlackBerry.
seo-title: Classe Adobe Mobile et référence de méthode
title: Adobe Mobile class and method reference
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

Classes et méthodes fournies par la bibliothèque BlackBerry.

The SDK currently has support for Adobe Analytics, and methods are in separate classes based on the solution.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

   * ADBMobilePrivacyStatusOptIn : les accès sont immédiatement envoyés.
   * ADBMobilePrivacyStatusOptOut : les accès sont ignorés.
   * ADBMobilePrivacyStatusUnknown : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`. Valeurs possibles :

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Renvoie l’identifiant d’utilisateur si un identifiant personnalisé a été défini. Returns `null` if a custom identifier is not set. La valeur par défaut est `null`.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static QString getUserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static bool getDebugLogging();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Définit la préférence de journalisation de débogage sur `debugLogging`.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/blackberry/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void collectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

* **trackState**

   Effectue le suivi de l’état d’une application avec les données contextuelles facultatives. Les états correspondent aux affichages disponibles dans l’application : tableau de bord d’accueil, paramètres d’application, panier, etc. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Effectue le suivi d’une action dans l’application. Les actions sont les événements qui se produisent dans l’application et que vous souhaitez mesurer, par exemple les connexions, les appuis sur la bannière, les abonnements aux flux, etc.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envoie les coordonnées x et y actuelles. Remplace l’événement par l’événement reçu de l’abonné à BPS.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` référence au fichier de configuration {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Requis) Une ou plusieurs suites de rapports où seront envoyées les données Analytics. Plusieurs identifiants de suite de rapports doivent être séparés par une virgule, sans espace.

   Voici un exemple de code pour cette variable :

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obligatoire). Serveur Analytics. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la variable `ssl`. Si `ssl` est défini sur `true`, une connexion sécurisée est établie avec le serveur. Si `ssl` est défini sur `false`, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). La valeur par défaut est `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Sinon, la propriété de configuration `offlineEnabled` *doit* être définie sur « false ». En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée, contactez Enterprise Support.[](https://helpx.adobe.com/contact/enterprise-support.ec.html)

   Si vous collectez actuellement des données AppMeasurement dans une suite de rapports qui collecte également des données depuis JavaScript, il est possible que vous deviez configurer une suite de rapports distincte pour les données mobiles ou que vous deviez inclure un horodatage personnalisé pour tous les accès JavaScript à l’aide de la variable `s.timestamp`.

   La valeur par défaut est `false`.

* **lifecycleTimeout**

   Spécifie la durée, en secondes, qui doit s’écouler entre les lancements de l’application pour qu’un lancement soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque l’application est placée en arrière-plan et réactivée. La durée passée en arrière-plan n’est pas prise en compte dans la durée de la session.

   La valeur par défaut est de 300 secondes.

* **batchLimit**

   Nombre maximal d’accès hors ligne stockés dans la file d’attente. The default value is 0 (No limit).

* **privacyDefault**

   * `optedin` - les accès sont envoyés immédiatement.
   * `optedout` - les accès sont ignorés.
   * `optunknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés).

      Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).
   Cette variable définit uniquement la valeur initiale. Si cette valeur est définie ou modifiée dans le code, la nouvelle valeur est utilisée jusqu’à ce qu’elle soit de nouveau modifiée, ou lorsque l’application est désinstallée, puis réinstallée.

   La valeur par défaut est `optedin`.

Voici un exemple de fichier `ADBMobileConfig.json` :

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```

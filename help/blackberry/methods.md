---
description: Classes et méthodes fournies par la bibliothèque BlackBerry.
seo-description: Classes et méthodes fournies par la bibliothèque BlackBerry.
seo-title: adobe Mobile, classe et référence de méthode
title: adobe Mobile, classe et référence de méthode
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 56%

---


# adobe Mobile, classe et référence de méthode {#adobe-mobile-class-and-method-reference}

Classes et méthodes fournies par la bibliothèque BlackBerry.

Le SDK prend actuellement en charge l’Adobe Analytics et les méthodes se trouvent dans des classes distinctes basées sur la solution.

## Paramètres du SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

   * ADBMobilePrivacyStatusOptIn : les accès sont envoyés immédiatement.
   * ADBMobilePrivacyStatusOptOut - les accès sont ignorés.
   * ADBMobilePrivacyStatusUnknown : si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

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

   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - Si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

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

## Méthodes Analytics {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

* **trackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. Les états sont les vues disponibles dans votre application, telles que &quot;tableau de bord d’accueil&quot;, &quot;paramètres de l’application&quot;, &quot;panier&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Effectue le suivi d’une action dans votre application. Les actions sont les actions qui se produisent dans votre application et que vous souhaitez mesurer, telles que les &quot;connexions&quot;, les &quot;clics sur la bannière&quot;, les &quot;abonnements de flux&quot; et d’autres mesures.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envoie les coordonnées x et y actuelles. Remplacez événement par le événement reçu de l’abonné à BPS.

   * Voici la syntaxe de cette méthode :

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json`Référence du fichier de configuration {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Obligatoire) Une ou plusieurs suites de rapports pour recevoir les données Analytics. Plusieurs ID de suite de rapports doivent être séparés par des virgules sans espace entre eux.

   Voici un exemple de code pour cette variable :

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obligatoire). Serveur Analytics. Cette variable doit être renseignée par le domaine du serveur, sans préfixe de protocole `https://` ou `https://`. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la `ssl` variable. Si `ssl` est`true` défini sur, une connexion sécurisée est établie avec le serveur. Si `ssl` est `false`défini sur, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères utilisé pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports.

* **ssl**

   Active (`true`) ou désactive (`false`) l&#39;envoi de données de mesure via SSL (HTTPS). La valeur par défaut est `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Si la suite de rapports n’est pas horodatée, la propriété de configuration `offlineEnabled` *doit* être définie sur « false ». En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée,  contactez  [Assistance](https://helpx.adobe.com/fr/contact/enterprise-support.ec.html)aux entreprises.

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   La valeur par défaut est `false`.

* **lifecycleTimeout**

   Indique la durée, en secondes, qui doit s’écouler entre les lancements de l’application avant que le lancement ne soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque votre application est envoyée en arrière-plan et réactivée. Le temps passé par votre application en arrière-plan n’est pas inclus dans la durée de session.

   La valeur par défaut est de 300 secondes.

* **batchLimit**

   Nombre maximal d’accès hors ligne stockés dans la file d’attente. La valeur par défaut est 0 (aucune limite).

* **privacyDefault**

   * `optedin` - les accès sont immédiatement envoyés.
   * `optedout` - les accès sont ignorés.
   * `optunknown` - Si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés).

      Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».
   Cette variable définit uniquement la valeur initiale. Si cette valeur est déjà définie ou modifiée dans le code, la nouvelle valeur est utilisée à partir de maintenant jusqu’à ce qu’elle soit modifiée ou que l’application soit désinstallée puis réinstallée.

   La valeur par défaut est `optedin`.

The following is an example of an `ADBMobileConfig.json` file:

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

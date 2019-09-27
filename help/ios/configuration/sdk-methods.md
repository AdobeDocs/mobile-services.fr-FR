---
description: Voici une liste des méthodes fournies par la bibliothèque iOS.
seo-description: Voici une liste des méthodes fournies par la bibliothèque iOS.
seo-title: Méthodes de configuration
solution: Marketing Cloud,Analytics
title: Méthodes de configuration
topic: Développeur et mise en œuvre
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

Voici une liste des méthodes fournies par la bibliothèque iOS.

The SDK currently has support for multiple Adobe Experience Cloud Solutions, including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service.

* **setAppExtensionType**

   Configure le paramètre du SDK Adobe Mobile de façon à déterminer le type d’extension en cours d’exécution.

   Valeurs possibles :
   * `ADBMobileAppExtensionTypeRegular` - extension is bundled with a containing app.
   * `ADBMobileAppExtensionTypeStandAlone` - n’est pas fournie avec une application contenant.
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Renvoie la version actuelle de la bibliothèque Adobe Mobile.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(NSString*) version;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel :

   * `ADBMobilePrivacyStatusOptIn` - les accès sont envoyés immédiatement.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).
La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`.

   Valeurs possibles :

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est `0`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Renvoie l’identifiant visiteur généré automatiquement. Il s’agit d’un identifiant visiteur unique propre à l’application qui est généré par les serveurs d’Adobe. Si les serveurs d’Adobe ne sont pas joignables au moment de la génération, l’identifiant est généré au moyen du CFUUID d’Apple. La valeur est générée au lancement initial, puis stockée et utilisée par la suite. Cet identifiant est conservé entre les mises à niveau de l’application, enregistré et restauré lors du processus de sauvegarde de l’application standard, puis supprimé lors de la désinstallation.

   >[!TIP]
   >
   >Si votre application effectue une mise à niveau d’Experience Cloud 3.x vers le SDK 4.x, l’identifiant visiteur personnalisé ou généré automatiquement précédent est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Pour plus d’informations, voir la ligne `userIdentifier` ci-dessous. Ceci permet de conserver les données visiteur entre les différentes mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `nil` et l’identifiant de suivi est utilisé.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Si un identifiant personnalisé a été défini, l’identifiant de l’utilisateur est renvoyé. Si aucun identifiant personnalisé n’est défini, la valeur `nil` est renvoyée. La valeur par défaut est `nil`.

   >[!TIP]
   >
   >Si votre application effectue une mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’identifiant visiteur personnalisé ou généré automatiquement précédent est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK.

   Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `nil` tant qu’il n’a pas été défini.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `NO`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Définit la préférence de journalisation de débogage sur `debug`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Indique au SDK que la prochaine reprise depuis l’arrière-plan ne doit pas commencer une nouvelle session, quelle que soit la valeur de temporisation de la session du cycle de vie dans le fichier de configuration.

   >[!TIP]
   >
   >Cette méthode est conçue pour être utilisée pour les applications qui s’inscrivent aux notifications en arrière-plan et qui doivent uniquement être appelées à partir du code qui s’exécute pendant que votre application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

   >[!TIP]
   >
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Vous permet de transmettre des données supplémentaires lors de la collecte de mesures de cycle de vie.

   Cette méthode doit être appelée à partir du point d’entrée de votre application. Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. Le SDK supprime du paramètre `NSDictionary` les valeurs qui ne sont pas de type `NSString` ou `NSNumber`. To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   Vous permet de charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application. Cette autre configuration est utilisée jusqu’à la fermeture de l’application.

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Définit le jeton d’appareil pour les notifications Push.

   >[!IMPORTANT]
   >
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Définit l’IDFA dans le SDK. L’IDFA est envoyé dans le cycle de vie s’il a été défini dans le SDK. Il est également accessible dans Signals (Signaux) (Postbacks).

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. Si vous récupérez l’IDFA, mais ne l’utilisez pas correctement, il est possible que votre application soit rejetée.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```


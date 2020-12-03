---
description: Voici une liste des méthodes fournies par la bibliothèque iOS.
seo-description: Voici une liste des méthodes fournies par la bibliothèque iOS.
seo-title: Méthodes de configuration
solution: Experience Cloud,Analytics
title: Méthodes de configuration
topic: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 100%

---


# Méthodes de configuration {#configuration-methods}

Voici une liste des méthodes fournies par la bibliothèque iOS.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform.

* **setAppExtensionType**

   Configure le paramètre SDK Mobile Adobe pour déterminer le type d’extension en cours d’exécution.

   Valeurs possibles :
   * `ADBMobileAppExtensionTypeRegular` - l’extension est regroupée avec une application contenante.
   * `ADBMobileAppExtensionTypeStandAlone` - l’extension n’est pas regroupée avec une application contenante.

   >[!TIP]
   >
   >Utilisez cette méthode **uniquement** si votre application possède une extension ou est une extension autonome. Pour plus d’informations, voir *ADBMobileAppExtensionType* ci-dessous.

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

   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).
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

   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

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

   Renvoie l’identifiant visiteur généré automatiquement. Il s’agit d’un identifiant de visiteur unique propre à l’application, généré par les serveurs d’Adobe. Si les serveurs d’Adobe ne peuvent pas être atteints au moment de la génération, alors l’identifiant est généré à l’aide du CFUUID d’Apple. La valeur est générée au lancement initial et stockée et utilisée à partir de ce point. Cet identifiant est conservé entre les mises à niveau de l’application, est enregistré et restauré pendant le processus de sauvegarde standard de l’application et est supprimé à la désinstallation.

   >[!TIP]
   >
   >Si votre application est mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’identifiant visiteur précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Pour plus d’informations, voir la ligne `userIdentifier` ci-dessous. Ceci permet de conserver les données visiteur entre les différentes mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `nil` et l’identifiant de suivi est utilisé.

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
   >Si votre application est mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’identifiant visiteur précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK.

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
   >Cette méthode est conçue pour les applications qui s’inscrivent aux notifications quand elles sont en arrière-plan et doit uniquement être appelée depuis le code qui s’exécute pendant que votre application se trouve en arrière-plan.

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
   >L’emplacement privilégié pour appeler cette méthode se trouve dans `application:didFinishLaunchingWithOptions:`.

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

   Cette méthode doit être appelée à partir du point d’entrée de votre application. Le cas échéant, la ou les méthodes `application:didFinishLaunchingWithOptions:` et/ou `applicationWillEnterForeground:` peuvent être incluses dans votre classe AppDelegate.

   >[!IMPORTANT]
   >
   >Les données transmises au SDK par l’intermédiaire de `collectLifecycleDataWithAdditionalData:` sont conservées dans `NSUserDefaults` par le SDK. Le SDK supprime du paramètre `NSDictionary` les valeurs qui ne sont pas de type `NSString` ou `NSNumber`. Pour utiliser `collectLifecycleDataWithAdditionalData:`, vous devez disposer de la **version 4.4** ou supérieure du SDK.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Utilisez cette API pour suspendre la collecte de données de cycle de vie. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

   >[!IMPORTANT]
   >
   >Dans la méthode `applicationDidEnterBackground` déléguée, vous devez d’abord appeler la méthode `pauseCollectingLifecycleData`.
   >
   >L’API est fournie pour atténuer le problème sur les iPhone 7/7s ou sur les appareils plus anciens dotés d’iOS 13, où la mesure de durée de session est devenue anormale. Cela est dû à des modifications inconnues survenues dans iOS 13, où iOS ne laisse pas assez de temps pour que la tâche en arrière-plan se termine lorsque vous mettez l’application en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Vous permet de charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application. Cette autre configuration est utilisée jusqu’à la fermeture de l’application.

   >[!IMPORTANT]
   >
   >Pour utiliser `overrideConfigPath`, vous devez disposer de la version 4.2 ou supérieure du SDK.

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
   >Cette méthode doit uniquement être utilisée dans la méthode `application:didRegisterForRemoteNotificationsWithDeviceToken:`.

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

   Définit l’IDFA dans le SDK. Si l’IDFA a été défini dans le SDK, il est envoyé dans le cycle de vie. L’IDFA est également accessible dans Signals (Postbacks).

   >[!TIP]
   >
   >Vous devez récupérer l’IDFA d’API Apple **uniquement** si vous utilisez un service publicitaire. Si vous récupérez l’IDFA, mais ne l’utilisez pas correctement, il est possible que votre application soit rejetée.
   >
   >Si votre application requiert un IDFA, consultez la [documentation d’Apple](https://developer.apple.com/documentation/adsupport) pour connaître les préférences de l’utilisateur en matière de suivi des publicités et pour récupérer la valeur de l’IDFA.
   >
   >Pour iOS 14+, le nouveau [framework de transparence du suivi des applications](https://developer.apple.com/documentation/apptrackingtransparency) doit être mis en œuvre afin de récupérer la valeur de l’IDFA.
   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
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


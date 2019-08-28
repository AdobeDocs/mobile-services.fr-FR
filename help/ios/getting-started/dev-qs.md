---
description: Ces informations vous aideront à mettre en œuvre la bibliothèque iOS et à collecter les mesures de cycle de vie, telles que les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.
seo-description: Ces informations vous aideront à mettre en œuvre la bibliothèque iOS et à collecter les mesures de cycle de vie, telles que les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.
seo-title: Mise en œuvre principale et cycle de vie
solution: Marketing Cloud, Analytics
title: Mise en œuvre principale et cycle de vie
topic: Développeur et mise en œuvre
uuid: 96 d 06325-e 424-4770-8659-4 b 5431318 ee 3
translation-type: tm+mt
source-git-commit: f39c18e48dc72e0ed8e8e35d962a1ae028055b87

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Ces informations vous aideront à mettre en œuvre la bibliothèque iOS et à collecter les mesures de cycle de vie, telles que les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.

## Téléchargement du kit SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**Condition requise**

Avant de télécharger le SDK, suivez les étapes de la section *Création d'une suite de rapports* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/requirements.md) pour configurer une suite de rapports de développement et télécharger une version prérenseignée du fichier de configuration.

Pour télécharger le kit SDK :

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h` : fichier d’en-tête Objective-C utilisé par AppMeasurement pour iOS.
   * `ADBMobileConfig.json` : fichier de configuration du SDK personnalisé pour votre application.
   * `AdobeMobileLibrary.a`, binaire gras compatible bitcode qui contient les versions de bibliothèque pour les périphériques ios (armv 7, armv 7 s, arm 64) et les simulateurs (i 386, x 86_ 64).

      Ce binaire gras doit être lié lorsque la cible est destinée à une application iOS.

   * `AdobeMobileLibrary_Extension.a` : binaire gras en bytecode contenant les versions de bibliothèque pour les appareils (armv7, armv7s et arm64) et les simulateurs (i386 et x86_64) iOS.

      Ce binaire gras doit être lié lorsque la cible est destinée à une extension iOS.

   * `AdobeMobileLibrary_Watch.a` : binaire gras en bytecode contenant les versions de bibliothèque pour les appareils (armv7k) et les simulateurs (i386, x86_64) Apple Watch.

      Ce binaire gras doit être lié lorsque la cible est destinée à une application d’extension Apple Watch (watchOS 2).

   * `AdobeMobileLibrary_TV.a` : binaire gras en bytecode contenant les versions de bibliothèque pour les nouveaux appareils (arm64) et le nouveau simulateur (x86_64) Apple TV.

      Ce binaire gras doit être lié lorsque la cible est destinée à une application Apple TV (tvOS).

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Xcode IDE et ouvrez votre application.
1. Dans Navigateur de projets, faites glisser le répertoire `AdobeMobileLibrary` sous votre projet.
1. Vérifiez les éléments suivants :

   * La case à cocher **[!UICONTROL Copier les éléments si nécessaire]est sélectionnée.**
   * **[!UICONTROL L’option Créer des groupes]** est sélectionnée.
   * Aucune des cases à cocher de la section **[!UICONTROL Ajouter aux cibles]n’est sélectionnée.**
   ![](assets/step_3.png)

1. Cliquez sur **[!UICONTROL Terminer]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. Cliquez sur votre application.
   1. Sous l’onglet **[!UICONTROL Général]**, sélectionnez vos cibles et liez les structures et bibliothèques requises dans les sections **[!UICONTROL Structures liées]et** Bibliothèques **.**
   * **Cibles d’une application iOS**
      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **Cibles d’une extension iOS**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Cible d’une application Apple Watch (watchOS 2)**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Cible d’une application Apple TV (tvOS)**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. Vérifiez qu’aucune erreur n’est générée lors de la création de votre application.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

Ajoutez un `collectLifecycleData``collectLifecycleDataWithAdditionalData` /e appel dans `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### Inclure des données supplémentaires avec des appels de cycle de vie

Pour ajouter des données aux appels de mesures de cycle de vie, utilisez `collectLifecycleDataWithAdditionalData` :

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. Le SDK retire du paramètre `NSDictionary` les valeurs qui ne sont pas de type `NSString` ou `NSNumber`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

Les valeurs des données contextuelles supplémentaires envoyées avec `collectLifecycleDataWithAdditionalData` doivent être mises en correspondance avec les variables personnalisées dans Adobe Mobile Services :

![](assets/map-variable-lifecycle.png)

Les autres mesures de cycle de vie sont collectées automatiquement. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

## Étapes suivantes {#section_A24DC703359D4B5C8F493D6421306FD3}

Exécutez les tâches ci-après :

* [Suivi des états de l’application](/help/ios/analytics-main/states.md)
* [Suivi des actions de l’application](/help/ios/analytics-main/actions.md)

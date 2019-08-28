---
description: À partir de la version WatchOS 2, vos extensions WatchKit s’exécutent sur un dispositif Apple Watch. Les applications qui s’exécutent dans cet environnement requièrent la structure WatchConnectivity pour partager des données avec leur application iOS contenante.
seo-description: À partir de la version WatchOS 2, vos extensions WatchKit s’exécutent sur un dispositif Apple Watch. Les applications qui s’exécutent dans cet environnement requièrent la structure WatchConnectivity pour partager des données avec leur application iOS contenante.
seo-title: Mise en œuvre de l’Apple Watch avec WatchOS 2
solution: Marketing Cloud, Analytics
title: Mise en œuvre de l’Apple Watch avec WatchOS 2
topic: Développeur et mise en œuvre
uuid: 9498467 e-db 5 e -411 e-a 00 e-d 19841 f 485 de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

À compter de watchos 2, les extensions watchkit peuvent s'exécuter sur Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>La version `AdobeMobileLibrary` 4.6.0 est `WatchConnectivity` prise en charge.

## Prise en main {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Assurez-vous d'avoir un projet avec au moins les cibles suivantes :
>
>* L’application contenante
>* L’application WatchKit
>* L’extension WatchKit
>



Pour en savoir plus sur le développement d’applications WatchKit, consultez [Architecture des applications pour montres](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configuration de l'application réceptrice {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier `AdobeMobileLibrary` dans votre projet.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application contenante, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Dans votre classe de mise en œuvre du protocole `UIApplicationDelegate`, ajoutez le protocole `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Importez `AdobeMobileLibrary` dans le fichier d’implémentation de votre classe de délégation d’application.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` est appelée dans `ADBMobile` la bibliothèque, qui renvoie un bool qui indique si le dictionnaire a été conçu pour une utilisation par la `ADBMobile` bibliothèque. Si `No` (Non) est renvoyé, le message n’a pas été lancé à partir du SDK Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Configuration de l'extension watchkit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre extension WatchKit, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importez `AdobeMobileLibrary` dans le fichier d’implémentation de votre classe de délégation d’extension.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Dans l’élément `applicationDidFinishLaunching` du délégué de votre extension, initialisez l’application Watch pour le SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` est appelée dans `ADBMobile` la bibliothèque, qui renvoie un bool qui indique si le dictionnaire a été conçu pour une utilisation par la `ADBMobile` bibliothèque. Si `NO` (Non) est renvoyé, le message n’a pas été lancé à partir du SDK Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Informations supplémentaires {#section_7BCDB5CF0D424DCA97883753D1881233}

À noter :

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* Les applications WatchKit fonctionnant sur une montre, leurs noms seront correctement indiqués dans `a.AppID`.
* Aucun appel de cycle de vie n’est déclenché sur les applications WatchOS2.


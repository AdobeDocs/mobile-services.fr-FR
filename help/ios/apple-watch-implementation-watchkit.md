---
description: À partir de la version WatchOS 2, vos extensions WatchKit s’exécuteront sur une Apple Watch. Les applications qui s’exécutent dans cet environnement requièrent le framework WatchConnectivity pour partager des données avec leur application iOS contenante.
seo-description: À partir de la version WatchOS 2, vos extensions WatchKit s’exécuteront sur une Apple Watch. Les applications qui s’exécutent dans cet environnement requièrent le framework WatchConnectivity pour partager des données avec leur application iOS contenante.
seo-title: Mise en œuvre de l’Apple Watch avec WatchOS 2
solution: Experience Cloud,Analytics
title: Mise en œuvre de l’Apple Watch avec WatchOS 2
topic: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '542'
ht-degree: 100%

---


# Mise en œuvre de l’Apple Watch avec WatchOS 2 {#apple-watch-implementation-with-watchos}

À partir de la version WatchOS 2, vos extensions WatchKit peuvent s’exécuter sur une Apple Watch. Les applications qui s’exécutent dans cet environnement requièrent la structure `WatchConnectivity` pour partager des données avec leur application iOS contenante.

>[!TIP]
>
>A partir de `AdobeMobileLibrary` v4.6.0, `WatchConnectivity` est pris en charge.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Prise en main {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Vérifiez que l’un de vos projets comprend au minimum les cibles suivantes :
>
>* L’application contenante
>* L’application WatchKit
>* L’extension WatchKit

>



Pour plus d’informations sur le développement d’applications WatchKit, voir [L’architecture des applications Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configuration de l’application conteneur {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier `AdobeMobileLibrary` dans votre projet.
1. Assurez-vous que le fichier `ADBMobileConfig.json` est membre de la cible de l’application contenante.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application contenante, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

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

1. Avant de lancer un appel vers la bibliothèque `ADBMobile`, dans `application:didFinishLaunchingWithOptions:` du délégué de votre application, configurez votre `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Mettez les méthodes `session:didReceiveMessage:` et `session:didReceiveUserInfo:` en œuvre dans le délégué de votre application.

   `syncSettings:` est appelé dans la bibliothèque `ADBMobile`, laquelle renvoie un booléen indiquant si le dictionnaire devait être utilisé par la bibliothèque `ADBMobile`. Si `No` (Non) est renvoyé, le message n’a pas été lancé à partir du SDK Adobe.

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

## Configuration de l’extension WatchKit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Vérifiez que le fichier `ADBMobileConfig.json` est un membre de la cible de votre extension WatchKit.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre extension WatchKit, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. Dans votre classe de mise en œuvre du protocole `WKExtensionDelegate`, importez `WatchConnectivity` et ajoutez le protocole `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importez `AdobeMobileLibrary` dans le fichier d’implémentation de votre classe de délégation d’extension.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Dans l’élément `applicationDidFinishLaunching` du délégué de votre extension, configurez `WCSession` avant de lancer des appels vers la bibliothèque `ADBMobile`.

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

1. Mettez les méthodes `session:didReceiveMessage:` et `session:didReceiveUserInfo:` en œuvre dans le délégué de votre extension.

   `syncSettings:` est appelé dans la bibliothèque `ADBMobile`, laquelle renvoie un booléen indiquant si le dictionnaire devait être utilisé par la bibliothèque `ADBMobile`. Si `NO` (Non) est renvoyé, le message n’a pas été lancé à partir du SDK Adobe.

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

* Pour les applications WatchKit, `a.RunMode` est défini sur `Extension`.
* Les applications WatchKit fonctionnant sur une montre, leurs noms seront correctement indiqués dans `a.AppID`.
* Aucun appel de cycle de vie n’est déclenché sur les applications WatchOS2.


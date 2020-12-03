---
description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.
seo-description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.
seo-title: Messagerie Push
solution: Experience Cloud,Analytics
title: Messagerie Push
topic: Developer and implementation
uuid: 2e2d8175-d7d0-4b6b-a14e-d419da1f9615
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---


# Messagerie Push {#push-messaging}

Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.

>[!IMPORTANT]
>
>Les informations de cette rubrique représentent une suggestion de mise en œuvre possible. Pour déterminer la mise en œuvre la plus appropriée à votre application, il est vivement recommandé de consulter la documentation iOS d’Apple. Votre mise en œuvre doit être déterminée par les structures que vous utilisez et les versions d’iOS que votre application va cibler.

Pour utiliser les messages push, vous **devez** disposer du SDK version 4.6 ou supérieure.

>[!IMPORTANT]
>
>Ne définissez pas manuellement l’Experience Cloud ID dans l’application. Ceci provoque la création d’un nouvel utilisateur unique qui ne recevra pas de messages push en raison de son état d’inclusion. Supposons, par exemple, qu’un utilisateur qui s’est abonné pour recevoir des messages push se connecte à votre application. Une fois connecté, si vous définissez manuellement l’identifiant dans votre application, un nouvel utilisateur unique est créé qui n’a pas choisi de recevoir de messages push. Ce nouvel utilisateur ne recevra pas vos messages Push.

## Conditions préalables  {#section_06655ABE973743DC965897B229A2118D}

* Ajoutez la bibliothèque à votre projet et mettez en œuvre les mesures de cycle de vie.

   Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).


* Le SDK doit être activé pour le service d’identification. Pour plus d’informations, voir [Configuration des options SDK du service d’identifications](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md).

>[!IMPORTANT]
>
>Vous ne pouvez pas déplacer votre application vers une nouvelle suite de rapports. Si vous migrez vers une nouvelle suite de rapports, votre configuration push peut devenir défaillante et les messages peuvent ne pas être envoyés.

## Activation de la messagerie push {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

1. Vérifiez que le fichier `ADBMobileConfig.json` contient les paramètres requis pour la messagerie push.

   La propriété `"marketingCloud"` de l’objet `"org"` doit être configurée pour la messagerie push.

   ```objective-c
   "marketingCloud": { 
       "org": "3CE342C92046435B0A490D4C@AdobeOrg" 
   }
   ```

1. Importez la bibliothèque dans votre `AppDelegate`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Pour déterminer les paramètres pour lesquels votre application doit demander une autorisation, voir [Support pour la configuration de la notification distante](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/HandlingRemoteNotifications.html#//apple_ref/doc/uid/TP40008194-CH6-SW1).

   Voici un exemple de mise en œuvre possible demandant l’autorisation d’utiliser les alertes, les badges, les sons et la notification à distance :

   ```objective-c
   // iOS 10 and newer 
   if (NSClassFromString(@"UNUserNotificationCenter")) { 
       UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];   
       [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
           completionHandler:^(BOOL granted, NSError * _Nullable error) { 
           if (granted) { NSLog(@"authorization given"); } 
           else { NSLog(@"authorization rejected"); } 
           if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
       }]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
       // make this class the delegate for user notification handling  
       center.delegate = self; 
   } 
   // iOS 8.0 to iOS 9.3.5 
   else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
   #pragma GCC diagnostic push 
   #pragma GCC diagnostic ignored "-Wdeprecated-declarations" 
       UIUserNotificationTypetypes = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
       UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
       [application registerUserNotificationSettings:settings]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
   } 
   // older than iOS 8.0  
   else { 
       [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound];  
   #pragma GCC diagnostic pop 
   }
   ```

1. Le jeton push doit être transmis au SDK à l’aide de la méthode `setPushIdentifier:` dans la classe ADBMobile.

   ```objective-c
   - (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
       ... 
       [ADBMobile setPushIdentifier:deviceToken]; 
       ... 
   }
   ```

1. Pour déterminer la bonne mise en œuvre pour votre environnement, voir [UserNotifications](https://developer.apple.com/documentation/usernotifications).

   Cette étape permet d’activer le reporting push en transmettant le dictionnaire `userInfo` au SDK lorsque l’utilisateur ouvre l’application en utilisant le clic publicitaire d’un message push.

   Le code ci-après est un exemple de mise en œuvre possible :

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

1. Pour conserver une estimation exacte de l’audience push, informez le SDK lorsqu’un utilisateur désactive manuellement les messages push de votre application en appelant `[ADBMobile setPushIdentifier: nil]` dans la méthode `applicationDidBecomeActive:` de votre `AppDelegate`.

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

## Exemple {#section_20BEA0D64F7C4D45A5EBEF21066E62AD}

L’exemple suivant montre à quoi pourrait ressembler la mise en œuvre d’un `AppDelegate.m` :

```objective-c
#import "AppDelegate.h" 
#import "ADBMobile.h" 
 
@implementation AppDelegate 
  
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    if (NSClassFromString(@"UNUserNotificationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
                              completionHandler:^(BOOL granted, NSError * _Nullable error) {  
            if (granted) { NSLog(@"authorization given"); } 
            else { NSLog(@"authorization rejected"); } 
            if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
        }]; 
        center.delegate = self; 
        [application registerForRemoteNotifications]; 
    } 
    else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
        UIUserNotificationType types = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
        UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
        [application registerUserNotificationSettings:settings];  
        [application registerForRemoteNotifications]; 
    } 
    else { 
        [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert| UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound]; 
#pragma GCC diagnostic pop 
    } 
 
    return YES; 
} 
 
- (void) applicationDidBecomeActive:(UIApplication *)application {  
    if (NSClassFromString(@"UNUserNotifcationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center getNotificationSettingsWithCompletionHandler:^(UNNotificationSettings * _Nonnull settings) { 
            if (settings.authorizationStatus != UNAuthorizationStatusAuthorized) {  
                [ADBMobile setPushIdentifier:nil]; 
            } 
        }]; 
    } 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
    else if ([application respondsToSelector:@selector(isRegisteredForRemoteNotifications)]) { 
        if (![application isRegisteredForRemoteNotifications]) {  
            [ADBMobile setPushIdentifier:nil]; 
        } 
    } 
    else if ([application enabledRemoteNotificationTypes] == UIRemoteNotificationTypeNone) { 
        [ADBMobile setPushIdentifier:nil]; 
    } 
#pragma GCC diagnostic pop 
} 
 
- (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
    [ADBMobile setPushIdentifier:deviceToken]; 
} 
 
- (void) application:(UIApplication *)application didFailToRegisterForRemoteNotificationsWithError:(NSError *)error { 
    [ADBMobile setPushIdentifier:nil]; 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    if (application.applicationState == UIApplicationStateInactive) {  
        [ADBMobile trackPushMessageClickThrough:userInfo];  
    } 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) {  
        if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
            [ADBMobile trackPushMessageClickThrough:userInfo]; 
        } 
    } 
 
    completionHandler(UIBackgroundFetchResultNoData); 
} 
 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
    } 
 
    completionHandler(); 
} 
 
@end
```

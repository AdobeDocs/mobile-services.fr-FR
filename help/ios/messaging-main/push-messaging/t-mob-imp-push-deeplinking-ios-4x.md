---
description: Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé adb_deeplink.
seo-description: Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé adb_deeplink.
seo-title: Mise en œuvre de la messagerie Push avec la création de liens profonds
title: Mise en œuvre de la messagerie Push avec la création de liens profonds
uuid: ee 9590 fc -8 bd 3-4111-9221-9011 d 9 edbd 84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé `adb_deeplink`.

1. Dans AppDelegate, vous pouvez récupérer l’URL de lien profond et la gérer par vous-même dans les emplacements suivants :

   * Dans `application:didFinishLaunchingWithOptions`:

      Si l’application n’est pas en cours d’exécution lorsqu’un clic publicitaire push se produit, vous pouvez récupérer les données utiles à partir de `launchOptions`. L’URL de lien profond se situe dans le dictionnaire des données utiles à côté de la clé `adb_deeplink`.

   * Méthodes déléguées pour les notifications distantes

      In the `didReceiveRemoteNotification:` application or in the `didReceiveRemoteNotification:fetchCompletionHandler:` application, you can get the URL by accessing the `userInfo` dictionary with the `adb_deeplink` key.

   * The delegate methods for `UNUserNotificationCenter`

      In the `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` method, you can get the push payload from the `userInfo` dictionary, in the `adb_deeplink` key.

Par exemple :

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```


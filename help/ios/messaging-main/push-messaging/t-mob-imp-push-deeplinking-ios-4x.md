---
description: Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé adb_deeplink.
title: Mise en oeuvre de la messagerie push avec la création de liens profonds
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
exl-id: c9ca955c-506f-45fe-82d6-fad2f9a80130
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 96%

---

# Mise en œuvre de la messagerie push avec la création de liens profonds {#implement-push-messaging-with-deep-linking}

Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé `adb_deeplink`.

1. Dans AppDelegate, vous pouvez récupérer l’URL de lien profond et la gérer par vous-même dans les emplacements suivants :

   * Dans `application:didFinishLaunchingWithOptions` :

      Si l’application n’est pas en cours d’exécution lorsqu’un clic publicitaire push se produit, vous pouvez récupérer les données utiles à partir de `launchOptions`. L’URL de lien profond se situe dans le dictionnaire des données utiles à côté de la clé `adb_deeplink`.

   * Méthodes déléguées pour les notifications distantes

      Dans l’application `didReceiveRemoteNotification:` ou `didReceiveRemoteNotification:fetchCompletionHandler:`, vous pouvez récupérer l’URL en accédant au dictionnaire `userInfo` à l’aide de la clé `adb_deeplink`.

   * Méthodes déléguées pour `UNUserNotificationCenter`

      Dans la méthode `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:`, vous pouvez obtenir la charge utile push à partir du dictionnaire `userInfo`, dans la clé `adb_deeplink`.

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

---
description: Utilisez ces informations pour effectuer un suivi des liens et des liens profonds dans vos applications mobiles à l’aide du SDK iOS Adobe Mobile.
seo-description: Utilisez ces informations pour effectuer un suivi des liens et des liens profonds dans vos applications mobiles à l’aide du SDK iOS Adobe Mobile.
seo-title: Suivi des liens profonds
solution: Experience Cloud,Analytics
title: Suivi des liens profonds
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 98%

---


# Suivi des liens profonds{#tracking-deep-links}

Utilisez ces informations pour effectuer un suivi des liens et des liens profonds dans vos applications mobiles à l’aide du SDK iOS Adobe Mobile.

Pour obtenir plus d’informations sur la façon dont les spécialistes du marketing utilisent des liens profonds dans leurs applications, consultez la section [Acquisition](/help/ios/acquisition-main/acquisition.md) de la documentation Mobile Services.

## Suivi des liens profonds

1. Ajoutez le SDK à votre projet et mettez en œuvre les mesures de cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Enregistrez l’application de façon à gérer les communications inter-applications ou la prise en charge des liens universels.

   Pour plus d’informations, voir [Communications inter-applications](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) ou [Prise en charge des liens universels](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Effectuez le suivi d’un lien profond dans openURL.

   Voici un exemple de suivi de lien profond :

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

Le SDK Adobe Mobile peut analyser les paires clé-valeur de données ajoutées à n’importe quel lien profond ou universel, à condition que le lien contienne une clé comportant une étiquette `a.deeplink.id` et une valeur correspondante non nulle générée par l’utilisateur. Toutes les paires clé-valeur de données ajoutées au lien seront analysées, associées à un accès de cycle de vie et envoyées à Adobe Analytics, à condition que le lien contienne une paire clé-valeur `a.deeplink.id`.

Vous pouvez également choisir d’ajouter une ou plusieurs des clés réservées suivantes (avec les valeurs générées par l’utilisateur) au lien profond ou universel :

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Ces clés sont des variables prémappées pour la création de rapports dans Adobe Analytics. Pour obtenir plus d’informations sur le mappage et les règles de traitement, voir [Règles de traitement et données contextuelles](/help/ios/getting-started/proc-rules.md).

### Suivi de liens profonds différés

1. Enregistrez le rappel de données Adobe.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Gérez `ADBMobileDataEventDeepLink` dans `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Informations publiques sur les liens profonds{#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Méthodes

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Constantes

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```


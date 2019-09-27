---
description: 'The following Acquisition methods are provided by the iOS library '
seo-description: 'The following Acquisition methods are provided by the iOS library '
seo-title: Méthodes d’acquisition
solution: Marketing Cloud,Analytics
title: Méthodes d’acquisition
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

Les méthodes d’acquisition suivantes sont fournies par la bibliothèque iOS :

La méthode suivante est prise en charge :

* **acquisitionCampaignStartForApp:data:**

   Permet aux développeurs de lancer une campagne d’acquisition d’applications, comme si l’utilisateur avait cliqué sur un lien. Cette méthode est utile pour créer des liens d’acquisition manuels et permettre à la boutique d’applications de vous rediriger, comme avec un `SKStoreView`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```



---
description: 'Les méthodes d’acquisition suivantes sont fournies par la bibliothèque iOS : '
seo-description: 'Les méthodes d’acquisition suivantes sont fournies par la bibliothèque iOS : '
seo-title: Méthodes d’acquisition
solution: Experience Cloud,Analytics
title: Méthodes d’acquisition
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 100%

---


# Méthodes d’acquisition{#acquisition-methods}

Les méthodes d’acquisition suivantes sont fournies par la bibliothèque iOS :

La méthode suivante est prise en charge :

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



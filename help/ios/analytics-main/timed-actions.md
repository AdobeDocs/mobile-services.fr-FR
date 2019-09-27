---
description: Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-description: Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-title: Actions minutées
solution: Marketing Cloud,Analytics
title: Actions minutées
topic: Développeur et mise en œuvre
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.

Les mesures suivantes sont rapportées dans les actions minutées :

* Nombre total de secondes dans l’application entre le début et la fin (intersessions)
* Nombre total de secondes entre le début et la fin (horloge)

Un rappel facultatif permet d’entreprendre des actions supplémentaires lorsque les actions minutées se terminent :

* Exécutez du code et ajoutez une logique (logique personnalisée facultative basée sur les résultats de durée).
* Ajoutez des données contextuelles avant de transmettre des durées.
* Annulez des accès et des durées qui n’ont pas encore été envoyés.

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans Mise en oeuvre [principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Appelez `trackTimedActionStart` et fournissez un nom d’action minutée et des données contextuelles facultatives.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Facultatif) Pour ajouter des données contextuelles supplémentaires à tout moment, vous pouvez appeler `trackTimedActionUpdate` avec le nom de l’action minutée.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Une fois l’événement terminé, appelez `trackTimedActionEnd` et transmettez le nom de l’action minutée, puis `TimedActionBlock` (rappel), qui recherche toutes les données et calcule les durées.

   Les mesures des événements minutés sont enregistrées dans des variables des solutions mobiles pour une création de rapports automatique.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre le nom de l’action minutée, vous pouvez envoyer des données contextuelles supplémentaires avec les appels de début et de mise à jour d’action :

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Context data values must be mapped to custom variables:

![](assets/map-variable-context-ltv.png)

## Exemple {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```


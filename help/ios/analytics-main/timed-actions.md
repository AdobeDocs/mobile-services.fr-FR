---
description: Les actions minutées vous permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée de chaque session et la durée totale d’une session à l’autre nécessaire à l’exécution de l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-description: Les actions minutées vous permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée de chaque session et la durée totale d’une session à l’autre nécessaire à l’exécution de l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-title: Actions minutées
solution: Experience Cloud,Analytics
title: Actions minutées
topic: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 100%

---


# Actions minutées {#timed-actions}

Les actions minutées vous permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée de chaque session et la durée totale d’une session à l’autre nécessaire à l’exécution de l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.

Les mesures suivantes sont signalées pour les actions minutées :

* Nombre total de secondes dans l’application entre le début et la fin (intersessions)
* Nombre total de secondes entre le début et la fin (heure de l’horloge)

Un rappel facultatif vous permet d’effectuer des actions supplémentaires lorsque l’action minutée se termine :

* Exécutez le code et ajoutez toute logique - logique personnalisée optionnelle basée sur les résultats de durée.
* Ajoutez des données contextuelles avant de transmettre des durées.
* Annuler l’accès et les durées pas encore envoyés.

## Suivi des actions minutées {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
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

## Envoi de données supplémentaires {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre le nom de l’action minutée, vous pouvez envoyer des données contextuelles supplémentaires avec les appels de début et de mise à jour d’action :

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Les valeurs des données contextuelles doivent être mises en correspondance avec des variables personnalisées :

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


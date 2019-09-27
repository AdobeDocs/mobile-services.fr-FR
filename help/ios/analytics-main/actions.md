---
description: Les actions sont des événements mesurables qui se produisent dans l’application. Chaque action est associée à une ou à plusieurs mesures qui sont incrémentées à chaque fois que l’événement se produit. Vous pouvez par exemple effectuer le suivi de chaque nouvel abonnement, chaque consultation d’un article ou chaque niveau atteint. Les mesures correspondantes pour ces événements sont configurées comme abonnements, articles lus et niveaux atteints.
seo-description: Les actions sont des événements mesurables qui se produisent dans l’application. Chaque action est associée à une ou à plusieurs mesures qui sont incrémentées à chaque fois que l’événement se produit. Vous pouvez par exemple effectuer le suivi de chaque nouvel abonnement, chaque consultation d’un article ou chaque niveau atteint. Les mesures correspondantes pour ces événements sont configurées comme abonnements, articles lus et niveaux atteints.
seo-title: Suivi des actions de l’application
solution: Marketing Cloud,Analytics
title: Suivi des actions de l’application
topic: Développeur et mise en œuvre
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Suivi des actions d’application {#track-app-actions}

Les actions sont des événements mesurables qui se produisent dans l’application. Chaque action est associée à une ou à plusieurs mesures qui sont incrémentées à chaque fois que l’événement se produit. Vous pouvez par exemple effectuer le suivi de chaque nouvel abonnement, chaque consultation d’un article ou chaque niveau atteint. Les mesures correspondantes pour ces événements sont configurées comme abonnements, articles lus et niveaux atteints.

Le suivi des actions n’est pas automatique. Pour effectuer le suivi d’un événement, vous devez appeler `trackAction`.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. Importez la bibliothèque.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Lorsque l’action dont vous souhaitez effectuer le suivi se produit dans votre application, appelez `trackAction` pour envoyer un accès pour cette action.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >If the code where you are adding this call might run while the app is in the background, call `trackActionFromBackground` instead of `trackAction`.

1. In the Adobe Mobile services UI, select your app and click **[!UICONTROL Manage App Settings]**.

1. Cliquez sur **[!UICONTROL Gérer les variables et les mesures]**, puis sur l’onglet **Mesures personnalisées[!UICONTROL .]**

1. Mappez le nom des données contextuelles utilisé dans votre code, par exemple `a.action=myapp.ActionName`, à un événement personnalisé.

   ![](assets/map-event-context-data.png)

Vous pouvez également définir une prop qui contiendra toutes les valeurs d’action en mappant une prop personnalisée dont le nom serait par exemple **[!UICONTROL Actions personnalisées]** et dont la valeur est définie sur `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

En plus du nom de l’action, vous pouvez envoyer des données contextuelles supplémentaires avec chaque appel d’action de suivi :

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Les valeurs de données contextuelles doivent être mises en correspondance avec des variables personnalisées :

![](assets/map-variable-context-action.png)

## Tracking background actions {#section_AC13013F207D4FBAAF27E4412034251E}

Si vous suivez une action dans un code qui pourrait être en cours d’exécution alors que l’application est en arrière-plan, appelez `trackActionFromBackground` plutôt que `trackAction`. Leurs paramètres sont identiques, mais `trackActionFromBackground` contient une logique supplémentaire pour éviter que les appels de cycle de vie ne se déclenchent alors qu’ils ne le devraient pas.

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Rapport |
|--- |--- |
| Adobe Mobile Services   | **** Rapport Chemins d’accès des actions. Affichez l’ordre dans lequel les actions se produisent dans l’application. Vous pouvez également cliquer sur **[!UICONTROL Personnaliser]dans n’importe quel rapport pour afficher les actions par ordre de classement, de tendances ou dans un rapport ventilé, ou appliquer un filtre afin d’afficher certaines actions pour un segment en particulier.** |
| Rapports et analyses marketing | **[!UICONTROL Rapport Événement personnalisé.]**  Une fois qu’une action est mise en correspondance avec un événement personnalisé, vous pouvez afficher les événements mobiles similaires à tous les autres événements Analytics. |
| Analyses ad hoc | **[!UICONTROL Rapport Événement personnalisé.]** Une fois qu’une action est mise en correspondance avec un événement personnalisé, vous pouvez afficher les événements mobiles similaires à tous les autres événements Analytics. |
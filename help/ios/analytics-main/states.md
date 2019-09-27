---
description: Les états correspondent aux différents écrans ou affichages de votre application. Chaque fois qu’un nouvel état s’affiche dans votre application (par exemple, lorsqu’un utilisateur navigue de la page d’accueil vers le fil d’actualité), vous devez envoyer un appel de suivi d’état. Dans iOS, le suivi des états se fait généralement au moyen de la méthode viewDidLoad de chaque affichage.
seo-description: Les états correspondent aux différents écrans ou affichages de votre application. Chaque fois qu’un nouvel état s’affiche dans votre application (par exemple, lorsqu’un utilisateur navigue de la page d’accueil vers le fil d’actualité), vous devez envoyer un appel de suivi d’état. Dans iOS, le suivi des états se fait généralement au moyen de la méthode viewDidLoad de chaque affichage.
seo-title: Suivi des états de l’application
solution: Marketing Cloud,Analytics
title: Suivi des états de l’application
topic: Développeur et mise en œuvre
uuid: 12cca4eb-1f15-4cec-a58f-76b69eaff99d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Suivi des états d’application {#track-app-states}

Les états correspondent aux différents écrans ou affichages de votre application. Chaque fois qu’un nouvel état s’affiche dans votre application (par exemple, lorsqu’un utilisateur navigue de la page d’accueil vers le fil d’actualité), vous devez envoyer un appel de suivi d’état. Dans iOS, le suivi des états se fait généralement au moyen de la méthode viewDidLoad de chaque affichage.

>[!TIP]
>
>To track states, make a call to `trackState`. Les états ne sont pas automatiquement suivis.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. Importez la bibliothèque.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Invoquez `trackState` afin d’envoyer un accès pour cet affichage d’état.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

Dans Adobe Mobile Services, le **[!UICONTROL State Name]** est reporté dans la variable *`View State`et un affichage est enregistré pour chaque appel*. `trackState` Dans d’autres interfaces Analytics, la variable **[!UICONTROL View State]** est signalée en tant que **[!UICONTROL Page Name]** et state views est signalée en tant que page views.

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

Context data values must be mapped to custom variables:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Les états sont généralement consultés au moyen d’un rapport de cheminement afin de découvrir comment les utilisateurs naviguent dans votre application et les états les plus vus.

|  |  |
|--- |--- |
| Adobe Mobile Services   | Rapport **[!UICONTROL Afficher les états.]** Ce rapport est basé sur les chemins que les utilisateurs prennent dans votre application. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Vous pouvez consulter les états sur les différents affichages des Pages : rapport **Pages**, rapport **[!UICONTROL Pages vues]** et rapport **Chemin[!UICONTROL .]** |
| Analyses ad hoc | Vous pouvez consulter les états sur les différents affichages des Pages au moyen de la dimension **Page**, de la mesure **[!UICONTROL Pages vues]** et des rapports **Chemin[!UICONTROL .]** |

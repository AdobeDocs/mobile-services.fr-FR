---
description: Ces informations vous permettent d’utiliser la messagerie intégrée (in-app) avec vos applications iOS.
seo-description: Ces informations vous permettent d’utiliser la messagerie intégrée (in-app) avec vos applications iOS.
seo-title: Messagerie in-app
solution: Marketing Cloud, Analytics
title: Messagerie in-app
topic: Développeur et mise en œuvre
uuid: 21 fa 6 a 94-bb 7 f -4 c 78-843 b-a 50 f 1974 db 22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-app messaging {#in-app-messaging}

Ces informations vous permettent d’utiliser la messagerie intégrée (in-app) avec vos applications iOS.

Vous **devez** disposer d’un SDK version 4.2 ou ultérieure pour utiliser la messagerie intégrée (in-app).

Informations à retenir :

* Les messages et les règles qui définissent le moment de l’affichage des messages sont créés dans Adobe Mobile Services. Pour plus d’informations, voir [Création d’un message in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Les mises à jour décrites dans cette section doivent être effectuées dans le SDK pour afficher les messages in-app.

   >[!TIP]
   >
   >Vous pouvez effectuer ces étapes même si aucun message n'est défini. Une fois les messages définis, ils sont diffusés dynamiquement vers votre application et affichés sans mise à jour de la boutique d'applications.

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/requirements.md).

1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for In-App messaging.
1. Pour les messages in-app à mettre à jour dynamiquement au lancement, l’objet `remotes` doit être présent et correctement configuré :

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` ou est `remotes` obligatoire.

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Pour plus d'informations, voir [Mise en œuvre principale et Cycle de vie](/help/ios/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Les SDK iOS Mobile Services effectuent le suivi des mesures suivantes pour vos messages in-app :

* Pour les messages in-app en plein écran et de type alerte :

   * **[!UICONTROL Impressions]**: lorsque l'utilisateur déclenche un message intégré.
   * **[!UICONTROL Clics publicitaires]**: lorsque l'utilisateur appuie sur le bouton **[!UICONTROL Clic publicitaire]** .
   * **[!UICONTROL Annuels]**: lorsque l'utilisateur appuie sur **[!UICONTROL le]** bouton Annuler.

* Pour les messages in-app personnalisés en plein écran, le contenu HTML du message doit contenir le code approprié pour notifier le suivi du SDK concernant les boutons suivants :

   * **[!UICONTROL Suivi des exemples de clics]** publicitaires (redirection) : `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Annuler]** (fermer) l'exemple de suivi : `adbinapp://cancel`

* Pour les notifications locales (à distance) :

   * **[!UICONTROL Impressions]** : lorsque l’utilisateur déclenche la notification.
   * **[!UICONTROL Ouverture]** : lorsque l’utilisateur ouvre l’application à partir de la notification.
   Voici un exemple sur la façon d’inclure le suivi ouvert :

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Lors de la création d’une image en plein écran dans Adobe Mobile Services, vous avez la possibilité de préciser une image de secours. Si votre message ne peut pas récupérer son image correspondante depuis le web, le SDK tente de charger l’image avec le même nom depuis votre offre d’applications. Ceci vous permet d’afficher votre message dans sa forme originale même si l’utilisateur est hors ligne ou si l’image prédéterminée est inaccessible.

Le nom de fichier de l’image de secours est spécifié lors de la configuration du message dans Adobe Mobile Services.

>[!IMPORTANT]
>
>Vous devez vous assurer que la ressource indiquée est disponible.


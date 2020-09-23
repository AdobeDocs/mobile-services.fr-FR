---
description: Ces informations vous aident à utiliser la messagerie in-app dans vos applications iOS.
seo-description: Ces informations vous aident à utiliser la messagerie in-app dans vos applications iOS.
seo-title: Messagerie in-app
solution: Experience Cloud,Analytics
title: Messagerie in-app
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 55%

---


# Messagerie in-app{#in-app-messaging}

Ces informations vous aident à utiliser la messagerie in-app dans vos applications iOS.

To use in-app messaging, you **must** have SDK version 4.2 or later.

Informations à retenir :

* Les messages et les règles qui définissent le moment où les messages sont affichés sont créés dans Adobe Mobile Services. For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Les mises à jour décrites dans cette section doivent être apportées au SDK pour afficher les messages in-app.

   >[!TIP]
   >
   >Vous pouvez suivre ces étapes même si vous n’avez aucun message défini. Une fois que vous avez défini les messages, ils sont envoyés dynamiquement à l’application et affichés sans mise à jour de la boutique d’applications.

## Activation de la messagerie in-app{#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/requirements.md).

1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vérifiez que le fichier `ADBMobileConfig.json` contient les paramètres requis pour la messagerie intégrée (in-app).
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
   >`messages` ou `remotes` est obligatoire.

   Si ces objets ne sont pas configurés, téléchargez un fichier `ADBMobileConfig.json` mis à jour depuis Adobe Mobile Services. Pour plus d’informations, voir [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/requirements.md).

## Suivi des messages in-app {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Les SDK iOS Mobile Services effectuent le suivi des mesures suivantes pour vos messages in-app :

* Pour les messages in-app en mode plein écran et en style d’alerte :

   * **[!UICONTROL Impressions]** : lorsque l’utilisateur déclenche un message in-app.
   * **[!UICONTROL Clics publicitaires]** : lorsque l’utilisateur appuie sur le bouton **[!UICONTROL Clic publicitaire]**.
   * **[!UICONTROL Annulations]** : lorsque l’utilisateur appuie sur le bouton **[!UICONTROL Annuler]**.

* Pour les messages in-app personnalisés en plein écran, le contenu HTML du message doit contenir le code approprié pour notifier le suivi du SDK concernant les boutons suivants :

   * Exemple de suivi des **[!UICONTROL Clics publicitaires]** (redirections) : `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Exemple de suivi - Annuler]** (fermer) : `adbinapp://cancel`

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

## Image de secours locale {#section_DEACC1CE549B4573B556A44A52409941}

Lors de la création d’un message en plein écran dans Adobe Mobile Services, vous pouvez éventuellement spécifier une image de secours. Si votre message ne parvient pas à récupérer l’image qui lui est destinée sur le Web, le SDK tente de charger l’image portant le même nom depuis votre lot d’applications. Vous pouvez ainsi afficher votre message sous sa forme d’origine, même si l’utilisateur est hors ligne ou si l’image prédéterminée est inatteignable.

Le nom du fichier d’image de secours est spécifié lors de la configuration du message dans Adobe Mobile Services.

>[!IMPORTANT]
>
>Vous devez vous assurer que la ressource spécifiée est disponible.


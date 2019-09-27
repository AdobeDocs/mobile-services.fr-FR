---
description: Vous pouvez configurer votre application pour utiliser le service de notifications Push Apple (APNS) ou Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
seo-title: Configure App to use APNS or FCM
solution: Marketing Cloud,Analytics
title: Configure App to use APNS or FCM
topic: Mesures
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configuration de votre application pour utiliser APNS ou FCM{#configure-app-to-use-apns-or-fcm}

Vous pouvez configurer votre application pour utiliser le service de notifications Push Apple (APNS) ou Firebase Cloud Messaging (FCM).

## Applications Android {#section_41D304102CDF4586911EC1413AD35A10}

### Si FCM n’est pas activé dans votre application

Pour configurer votre application Android afin d’utiliser FCM dans ce scénario :

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Cliquez sur **[!UICONTROL Commencer]** et sélectionnez **[!UICONTROL Ajouter un projet]**.

1. Entrez un nom de projet et, si vous optez pour Google Analytics pour les données Firebase, cochez la case acceptant les termes du contrôleur.

1. Cliquez sur **[!UICONTROL Créer un projet]** et attendez la création du projet.

1. Cliquez sur le projet créé pour afficher la page Aperçu **[!UICONTROL du]** projet pour le projet créé. Click the button with the Android icon to add an Android app to the project.

1. Enter the app package name, app nickname, and signing certificate if needed.

1. Follow the additional steps suggested by the setup wizard. After verifying the Firebase setup by testing communication with the Firebase servers, return to the **[!UICONTROL Project Overview]** page.

1. Click the gear icon to the right of the Project Overview button and click Project Settings.********

1. Click the Cloud Messaging tab.****

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Par exemple :

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### If FCM is enabled in your app

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Click **[!UICONTROL Get Started]**. This will open the project index page. Recherchez le projet Firebase activé lié à votre application Android et cliquez sur la carte du projet.

1. The Project Overview for the project should then be loaded. **** Click the gear icon to the right of the Project Overview button and click Project Settings.********

1. Click the **[!UICONTROL Cloud Messaging]** tab.

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Par exemple :

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Pour configurer votre application iOS en vue de l’utilisation du service APNS :

1. Rendez-vous sur [https://developer.apple.com/account](https://developer.apple.com/account) et connectez-vous à votre [compte Apple Developer](https://developer.apple.com/account).
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. Si vous avez configuré un ID d’application pour la diffusion push, passez à l’étape 11.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. Saisissez une description pour l’ID d’application.
1. Saisissez un suffixe pour l’ID d’application.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. Sous **[!UICONTROL Services de l’application]**, cochez la case **[!UICONTROL Notifications Push]**.
1. Click **[!UICONTROL Continue]**.
1. Cliquez sur **[!UICONTROL Envoyer]**.
1. Cliquez sur **[!UICONTROL Terminé]**.
1. Sélectionnez votre ID d’application configuré pour utiliser la messagerie Push dans la liste et cliquez sur **[!UICONTROL Modifier]**.
1. Si un certificat push a déjà été créé, passez directement à l’étape 15.
1. Faites défiler l’écran jusqu’à **[!UICONTROL Notifications Push]** et cliquez sur le bouton **[!UICONTROL Créer un certificat…]**.

   The button you click depends whether you are creating a certificate for Development or Production.
1. Follow the steps on how to create your CSR on Apple's website, upload the CSR, and generate your certificate.
1. Faites défiler jusqu’à la section **[!UICONTROL Notifications Push]** et téléchargez le certificat SSL que vous venez de créer.
1. Cliquez deux fois sur le certificat téléchargé pour l’ajouter à votre Keychain.

### Certificat SSL et clés privées

Pour obtenir votre certificat SSL et votre clé privée (APNS) :

1. Ouvrez **[!UICONTROL Accès au trousseau]**.
1. Cliquez sur **[!UICONTROL Mes certificats]** et recherchez le **[!UICONTROL certificat de services iOS]** approprié pour votre application et votre environnement.

   Vous pouvez identifier le certificat approprié en associant l’ID du lot et en indiquant s’il s’agit d’un certificat de développement ou de production.

1. Développez le certificat et vérifiez qu’il contient une clé privée.
1. Effectuez un clic droit sur la clé privée et sélectionnez **[!UICONTROL Export "*`<name of key>`*]**.
1. Type the necessary information in the dialog box and save your new  file.`.p12`

   Aucun mot de passe n’est requis.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.


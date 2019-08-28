---
description: Vous pouvez configurer votre application pour qu'elle utilise le service Apple Push Notification (APNS) ou Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: Vous pouvez configurer votre application pour qu'elle utilise le service Apple Push Notification (APNS) ou Firebase Cloud Messaging (FCM).
seo-title: Configuration de l'application pour utiliser APNS ou FCM
solution: Marketing Cloud, Analytics
title: Configuration de l'application pour utiliser APNS ou FCM
topic: Mesures
uuid: fa 411 f 2 a-ba 47-4499-bbe 5-1 aedef 6 b 49 ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configuration de l'application pour utiliser APNS ou FCM{#configure-app-to-use-apns-or-fcm}

Vous pouvez configurer votre application pour qu'elle utilise le service Apple Push Notification (APNS) ou Firebase Cloud Messaging (FCM).

## Applications Android {#section_41D304102CDF4586911EC1413AD35A10}

### Si FCM n'est pas activé dans votre application

Pour configurer votre application Android pour qu'elle utilise FCM dans ce scénario :

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Cliquez **[!UICONTROL sur Démarrer]** et sélectionnez **[!UICONTROL Ajouter un projet]**.

1. Saisissez le nom d'un projet et, si vous sélectionnez Google Analytics pour les données Firebase, cochez la case acceptant les termes du contrôleur de contrôle.

1. Cliquez **[!UICONTROL sur Créer un projet]** et attendez que le projet soit créé.

1. Cliquez sur le projet créé et la page **[!UICONTROL Aperçu]** du projet pour le projet créé doit être affichée. Cliquez sur le bouton avec l'icône Android pour ajouter une application Android au projet.

1. Si nécessaire, saisissez le nom du pack de l'application, le surnom de l'application et le certificat de signature.

1. Suivez les étapes supplémentaires suggérées par l'assistant de configuration. Après avoir vérifié la configuration de Firebase en testant la communication avec les serveurs Firebase, revenez à **[!UICONTROL la page Aperçu]** du projet.

1. Cliquez sur l'icône représentant un engrenage à droite **[!UICONTROL du bouton Aperçu]** du projet, puis cliquez sur **[!UICONTROL Paramètres du projet]**.

1. Cliquez sur l'onglet **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Par exemple :

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Si FCM est activé dans votre application

Pour configurer votre application Android pour qu'elle utilise FCM dans ce scénario :

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Cliquez **[!UICONTROL sur Démarrer]**. Cette opération ouvre la page d'index du projet. Recherchez le projet Firebase activé dans votre application Android et cliquez sur la carte du projet.

1. L'aperçu **[!UICONTROL du projet]** pour le projet doit alors être chargé. Cliquez sur l'icône représentant un engrenage à droite **[!UICONTROL du bouton Aperçu]** du projet, puis cliquez sur **[!UICONTROL Paramètres du projet]**.

1. Cliquez sur l'onglet **[!UICONTROL Cloud Messaging]** .

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
1. Si vous avez configuré un ID d'application pour le mode Push, passez à l'étape 11.
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

   Le bouton sur lequel vous cliquez dépend de la création d'un certificat pour le développement ou la production.
1. Suivez la procédure de création de votre CSR sur le site Web d'Apple, téléchargez la CSR et générez votre certificat.
1. Faites défiler jusqu’à la section **[!UICONTROL Notifications Push]** et téléchargez le certificat SSL que vous venez de créer.
1. Cliquez deux fois sur le certificat téléchargé pour l'ajouter à votre chaîne clé.

### Certificat SSL et clés privées

Pour obtenir votre certificat SSL et votre clé privée (APNS) :

1. Ouvrez **[!UICONTROL Accès au trousseau]**.
1. Cliquez sur **[!UICONTROL Mes certificats]** et recherchez le **[!UICONTROL certificat de services iOS]** approprié pour votre application et votre environnement.

   Vous pouvez identifier le certificat approprié en associant l’ID du lot et en indiquant s’il s’agit d’un certificat de développement ou de production.

1. Développez le certificat et vérifiez qu’il contient une clé privée.
1. Effectuez un clic droit sur la clé privée et sélectionnez **[!UICONTROL Export "*`<name of key>`*]**.
1. Saisissez les informations nécessaires dans la boîte de dialogue et enregistrez le nouveau `.p12` fichier.

   Aucun mot de passe n’est requis.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.


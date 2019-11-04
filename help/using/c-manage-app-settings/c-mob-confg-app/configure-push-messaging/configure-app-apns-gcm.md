---
description: Vous pouvez configurer votre application pour utiliser l’Apple Push Notification Service (APNS) ou Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: Vous pouvez configurer votre application pour utiliser l’Apple Push Notification Service (APNS) ou Firebase Cloud Messaging (FCM).
seo-title: Configuration de votre application pour utiliser APNS ou FCM
solution: Experience Cloud,Analytics
title: Configuration de votre application pour utiliser APNS ou FCM
topic: Mesures
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: ht
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configuration de votre application pour utiliser APNS ou FCM{#configure-app-to-use-apns-or-fcm}

Vous pouvez configurer votre application pour utiliser l’Apple Push Notification Service (APNS) ou Firebase Cloud Messaging (FCM).

## Applications Android {#section_41D304102CDF4586911EC1413AD35A10}

### Si FCM n’est pas activé dans votre application

Pour configurer votre application Android afin d’utiliser FCM dans ce scénario :

1. Accédez à [https://firebase.google.com/](https://firebase.google.com/) et connectez-vous avec vos identifiants Google Dev.

1. Cliquez sur **[!UICONTROL Commencer]** et sélectionnez **[!UICONTROL Ajouter un projet]**.

1. Saisissez un nom de projet et, si vous optez pour Google Analytics pour les données Firebase, cochez la case acceptant les termes contrôleur-contrôleur.

1. Cliquez sur **[!UICONTROL Créer un projet]** et attendez la création du projet.

1. Cliquez sur le projet créé pour afficher la page **[!UICONTROL Aperçu du projet]** pour le projet créé. Cliquez sur le bouton avec l’icône Android pour ajouter une application Android au projet.

1. Si nécessaire, saisissez le nom du pack d’application, le surnom de l’application et le certificat de signature.

1. Suivez les étapes supplémentaires suggérées par l’assistant de configuration. Après avoir vérifié la configuration de Firebase en testant la communication avec les serveurs Firebase, revenez à la page **[!UICONTROL Aperçu du projet]**.

1. Cliquez sur l’icône d’engrenage à droite du bouton **[!UICONTROL Aperçu du projet]** et cliquez sur **[!UICONTROL Paramètres du projet]**.

1. Cliquez sur l’onglet **[!UICONTROL Cloud Messaging]**.

1. Copiez la **[!UICONTROL clé serveur héritée]** et l’**[!UICONTROL ID d’expéditeur]** afin de les réutiliser ultérieurement.

   Par exemple :

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Si FCM est activé dans votre application

Pour configurer votre application Android afin d’utiliser FCM dans ce scénario :

1. Accédez à [https://firebase.google.com/](https://firebase.google.com/) et connectez-vous avec vos identifiants Google Dev.

1. Cliquez sur **[!UICONTROL Commencer]**. La page index du projet s’ouvre alors. Recherchez le projet pour lequel Firebase est activé et qui est lié à votre application Android, puis cliquez sur la carte du projet.

1. L’**[!UICONTROL Aperçu du projet]** doit ensuite être chargé. Cliquez sur l’icône d’engrenage à droite du bouton **[!UICONTROL Aperçu du projet]** et cliquez sur **[!UICONTROL Paramètres du projet]**.

1. Cliquez sur l’onglet **[!UICONTROL Cloud Messaging]**.

1. Copiez la **[!UICONTROL clé serveur héritée]** et l’**[!UICONTROL ID d’expéditeur]** afin de les réutiliser ultérieurement.

   Par exemple :

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## applications iOS {#section_2031DAB485FC4D2B9027E42AD90B294D}

Pour configurer votre application iOS en vue de l’utilisation du service APNS :

1. Rendez-vous sur [https://developer.apple.com/account](https://developer.apple.com/account) et connectez-vous à votre [compte Apple Developer](https://developer.apple.com/account).
1. Sous **[!UICONTROL Applications iOS]**, sélectionnez **[!UICONTROL Identifiants]**.
1. Si vous possédez un ID d’application configuré pour les notifications push, allez à l’étape 11.
1. Appuyez sur le bouton **[!UICONTROL +]** pour créer un nouvel ID d’application.
1. Saisissez une description pour l’ID d’application.
1. Saisissez un suffixe pour l’ID d’application.

   >[!IMPORTANT]
   >
   >Pour permettre la prise en charge des notifications push, vous devez utiliser un ID d’application explicite ne contenant **aucun** caractère générique (par exemple `- com.tester.pushSample`).

1. Sous **[!UICONTROL Services de l’application]**, cochez la case **[!UICONTROL Notifications Push]**.
1. Cliquez sur **[!UICONTROL Continuer]**.
1. Cliquez sur **[!UICONTROL Envoyer]**.
1. Cliquez sur **[!UICONTROL Terminé]**.
1. Sélectionnez votre ID d’application configuré pour utiliser la messagerie Push dans la liste et cliquez sur **[!UICONTROL Modifier]**.
1. Si un certificat push a déjà été créé, passez directement à l’étape 15.
1. Faites défiler l’écran jusqu’à **[!UICONTROL Notifications Push]** et cliquez sur le bouton **[!UICONTROL Créer un certificat…]**.

   Le bouton sur lequel vous cliquez varie selon que vous créez un certificat pour le développement ou la production.
1. Suivez les étapes de création de votre CSR sur le site Web d’Apple, chargez la CSR et générez votre certificat.
1. Faites défiler jusqu’à la section **[!UICONTROL Notifications Push]** et téléchargez le certificat SSL que vous venez de créer.
1. Double-cliquez sur le certificat téléchargé pour l’ajouter à votre système Keychain.

### Certificat SSL et clés privées

Pour obtenir votre certificat SSL et votre clé privée (APNS) :

1. Ouvrez **[!UICONTROL Accès au trousseau]**.
1. Cliquez sur **[!UICONTROL Mes certificats]** et recherchez le **[!UICONTROL certificat de services iOS]** approprié pour votre application et votre environnement.

   Vous pouvez identifier le certificat approprié en associant l’ID du lot et en indiquant s’il s’agit d’un certificat de développement ou de production.

1. Développez le certificat et vérifiez qu’il contient une clé privée.
1. Effectuez un clic droit sur la clé privée et sélectionnez **[!UICONTROL Export "*`<name of key>`*]**.
1. Saisissez les informations nécessaires dans la boîte de dialogue et enregistrez votre nouveau fichier `.p12`.

   Aucun mot de passe n’est requis.

1. Dans **[!UICONTROL Clé privée]**, saisissez le fichier `.p12`.


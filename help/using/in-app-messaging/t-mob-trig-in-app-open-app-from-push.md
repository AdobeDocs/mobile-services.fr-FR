---
description: Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.
seo-description: Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.
seo-title: Déclencher un message in-app lorsque l’application est ouverte à partir d’un message push
title: Déclencher un message in-app lorsque l’application est ouverte à partir d’un message push
uuid: e 1 c 8 e 29 d -1 c 2 b -47 b 2-8 ab 2-6 b 6 e 15 df 86 f 6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7

---


# Trigger an in-app message when the app is opened from a push message{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.

1. Obtenez l’ID du message push qui sera envoyé à l’utilisateur.

   L’ID de message push se trouve dans l’URL du processus de création de message.

   Voici un exemple :

   ![](assets/brandon_task1.png)

1. Sauvegardez et activez le message in-app avec le déclencheur suivant : 

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >L'ID de message push est l'identifiant que vous avez indiqué à l'étape 1.

   Ce déclencheur doit être ajouté manuellement car il ne se trouve pas dans la liste déroulante **[!UICONTROL Déclencheur].**

   ![](assets/brandon_task2.png)

1. Sauvegardez et envoyez le message push dont l’ID push correspond à celui que vous avez identifié à l’étape 1.
1. Cliquez sur le message push pour ouvrir l’application et vérifier que le message in-app s’affiche bien à l’ouverture.

   Lors des phases de test, gardez les informations suivantes à l’esprit :

   * Une fois le message in-app sauvegardé, la mise à jour du fichier de configuration hébergé avec le nouveau message prend environ 45 secondes.
   * L’application recherche les mises à jour du fichier de configuration (le nouveau message in-app) chaque fois qu’un **nouveau** lancement est effectué. Vous devez donc vous assurer que l’application amorce un nouveau lancement lorsqu’un clic est effectué sur le message push.
   Cela signifie généralement que vous devez vous assurer que l’expiration de la session a bien eu lieu. Le délai d’expiration par défaut est de 5 minutes.


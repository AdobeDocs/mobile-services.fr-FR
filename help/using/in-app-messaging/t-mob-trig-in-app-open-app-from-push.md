---
description: Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.
seo-description: Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.
seo-title: Déclencher un message intégré lorsque l’application est ouverte à partir d’un message Push
title: Déclencher un message intégré lorsque l’application est ouverte à partir d’un message Push
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 59%

---


# Déclenchement d’un message in-app lorsque l’application est ouverte à partir d’un message push{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

Vous pouvez définir l’ID de message push envoyé lorsqu’un utilisateur ouvre l’application à partir d’un message push en tant que déclencheur de message in-app.

1. Obtenez l’ID du message push qui sera envoyé à l’utilisateur.

   L’ID du message Push se trouve dans l’URL pendant le processus de création du message.

   Voici un exemple :

   ![](assets/brandon_task1.png)

1. Sauvegardez et activez le message in-app avec le déclencheur suivant :

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >L’ID de message push est l’ID que vous avez identifié à l’étape 1.

   Ce déclencheur doit être ajouté manuellement car il ne se trouve pas dans la liste déroulante **[!UICONTROL Déclencheur]**.

   ![](assets/brandon_task2.png)

1. Sauvegardez et envoyez le message push dont l’ID push correspond à celui que vous avez identifié à l’étape 1.
1. Cliquez sur le message push pour ouvrir l’application et vérifier que le message in-app s’affiche bien à l’ouverture.

   Pendant le test, tenez compte des informations suivantes :

   * Après avoir enregistré le message in-app, le fichier de configuration hébergé met environ 45 secondes à se mettre à jour avec le nouveau message.
   * L’application recherche les mises à jour du fichier de configuration (le nouveau message intégré à l’application) lorsqu’un **nouveau** lancement se produit. Vous devez donc vous assurer que l’application déclenche un nouveau lancement lorsque l’utilisateur clique sur le message push.

   Cela signifie généralement que vous devez vous assurer que le délai d’expiration de la session s’est produit. Le délai par défaut est de 5 minutes.


---
description: Ces informations vous aideront à résoudre les problèmes liés aux messages push.
keywords: mobile
solution: Experience Cloud,Analytics
title: Dépannage de la messagerie Push
topic-fix: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
exl-id: 82b89f56-f43e-4b0d-80c5-5bff4013e5f7
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Résolution des problèmes liés aux messages push {#troubleshooting-push-messaging}

Ces informations vous aideront à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* Attente des accès Analytics

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. La valeur par défaut est de 1 heure sur l’heure en cours. Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. À titre d’exemple, une suite de rapports traite les correspondances toutes les heures. Si vous tenez compte du temps de traitement de 30 minutes au maximum, il peut s’écouler jusqu’à 90 minutes avant qu’un accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur d’Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* Attente du service Push

   Le service Push (APNS ou FCM) n’envoie pas toujours immédiatement le message. Bien que cela soit rare, nous avons constaté un retard de 5 à 10 minutes. Sur la page Messages, vous pouvez vérifier que le message push a été envoyé au service Push en cliquant sur le lien **[!UICONTROL Afficher]** du message. Dans le rapport, le nombre d’envois vers le service Push réussis est indiqué dans la colonne **[!UICONTROL Publié]**.

   >[!TIP]
   >
   >Les services push ne garantissent pas qu’un message sera envoyé.

   Pour obtenir plus d’informations sur la fiabilité des services, voir la documentation appropriée :

   * **APNS** : [Qualité du service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM** : [Durée de vie d’un message](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Pourquoi mes messages push sont-ils coupés ou ne se développent-ils pas ?

Pour certains appareils Android, vous devrez peut-être utiliser `NotificationCompat.BigTextStyle` pour l’affichage des messages.

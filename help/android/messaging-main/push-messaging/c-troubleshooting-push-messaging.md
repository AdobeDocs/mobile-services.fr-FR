---
description: Ces informations vous aideront à résoudre les problèmes liés aux messages push.
keywords: mobile
seo-description: Ces informations vous aideront à résoudre les problèmes liés aux messages push.
seo-title: Résolution des problèmes de messagerie Push
solution: Marketing Cloud,Analytics
title: Résolution des problèmes de messagerie Push
topic: Mesures
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Résolution des problèmes de messagerie push {#troubleshooting-push-messaging}

Ces informations vous aideront à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* Attente des accès Analytics

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. La valeur par défaut est de 1 heure sur l’heure en cours. Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. À titre d’exemple, une suite de rapports traite les accès toutes les heures. Si vous tenez compte d’une durée de traitement d’un maximum de 30 minutes, cela pourrait prendre jusqu’à 90 minutes pour qu’un accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur d’Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* Attente du service Push

   The push service (APNS or FCM) might not immediately send out the message. Bien que cela soit rare, nous avons constaté un retard de 5 à 10 minutes. Sur la page Messages, vous pouvez vérifier que le message push a été envoyé au service Push en cliquant sur le lien **Afficher** du message. Dans le rapport, le nombre d’envois vers le service Push réussis est indiqué dans la colonne **[!UICONTROL Publié].**

   >[!TIP]
   >
   >The push services do not guarantee that a message will be sent.

   Pour obtenir plus d’informations sur la fiabilité des services, voir la documentation appropriée :

   * **APNS** : [Qualité de service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: Durée de [vie d’un message](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Pourquoi mes messages push sont-ils coupés ou ne se développent-ils pas ?

Pour certains appareils Android, vous devrez peut-être utiliser `NotificationCompat.BigTextStyle` pour l’affichage des messages.

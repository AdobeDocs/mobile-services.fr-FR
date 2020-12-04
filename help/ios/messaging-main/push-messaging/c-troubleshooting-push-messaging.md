---
description: Ces informations vous aideront à résoudre les problèmes liés aux messages push.
keywords: mobile
seo-description: Ces informations vous aideront à résoudre les problèmes liés aux messages push.
seo-title: Résolution des problèmes liés aux messages push
solution: Experience Cloud,Analytics
title: Résolution des problèmes liés aux messages push
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 100%

---


# Résolution des problèmes liés aux messages push {#troubleshooting-push-messaging}

Ces informations vous aideront à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* **Attente des accès Analytics**

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. La valeur par défaut est de 1 heure sur l’heure en cours. Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes.

   À titre d’exemple, une suite de rapports traite les correspondances toutes les heures. Si vous tenez compte du temps de traitement de 30 minutes au maximum, il peut s’écouler jusqu’à 90 minutes avant qu’un accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur d’Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* **Attente du service Push**

   Le service push (APNS ou GCM) n’envoie pas toujours le message immédiatement. Bien que cela soit rare, nous avons constaté un retard de 5 à 10 minutes. Sur la page Messages, vous pouvez vérifier que le message push a été envoyé au service Push en cliquant sur le lien Afficher du message. Dans le rapport, le nombre d’envois vers le service Push réussis est indiqué dans la colonne Publié.

   >[!TIP]
   >
   >Les services Push ne garantissent pas qu’un message sera envoyé. Pour obtenir plus d’informations sur la fiabilité des services, voir la documentation appropriée :
   >
   >* **APNS** : [Qualité du service](https://developer.apple.com/documentation/usernotifications)
   >
   >* **GCM** : [Durée de vie d’un message](https://developers.google.com/cloud-messaging/concept-options)


## Comment renouveler mon certificat du service Apple Push ?

L’envoi de messages push nécessite un certificat de service Push valide. Mobile Services vous avertit lorsque votre certificat est expiré ou sur le point d’expirer. Si vous recevez cet avertissement, suivez la procédure suivante pour renouveler votre certificat :

1. Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.
2. Pour supprimer le certificat actuel, faites défiler jusqu’à **[!UICONTROL Services Push]**, puis cliquez sur **[!UICONTROL Supprimer]**.
3. Configurez et testez un nouveau certificat.

   Pour plus d’informations, voir [Conditions préalables requises pour activer la messagerie push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Cliquez sur **[!UICONTROL Enregistrer]**.

## Pourquoi est-ce que je ne vois pas mes messages push dans un simulateur iOS ?

Les simulateurs iOS ne prennent pas en charge les messages push.

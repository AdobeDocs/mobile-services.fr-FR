---
description: Vous pouvez afficher des rapports sur les messages in-app et push.
keywords: mobile
seo-description: Vous pouvez afficher des rapports sur les messages in-app et push.
seo-title: Afficher les rapports sur les messages
solution: Marketing Cloud,Analytics
title: Afficher les rapports sur les messages
topic: Mesures
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Vous pouvez afficher des rapports sur les messages in-app et push.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   For more information about creating a sticky filter, see Add a sticky filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)

>[!TIP]
>
>Selon le type de message affiché, le rapport peut varier.

## Les messages in-app {#section_90B79BA58E8141F78538C187EB1BF8C7}

Si vous affichez des rapports pour un message in-app, le rapport ressemble à l’illustration suivante :

![message de rapport](assets/report_message.png)

### Mesures des messages in-app

Voici la liste des mesures disponibles pour les messages in-app :

* **[!UICONTROL Impression]**, lorsqu’un message est déclenché.

* **[!UICONTROL Clic publicitaire]**, lorsqu’un utilisateur appuie sur le bouton **[!UICONTROL Clic publicitaire]** d’une alerte ou d’un message en plein écran et lorsqu’un utilisateur ouvre l’application à partir d’une notification locale.

* **[!UICONTROL Annuler]**, lorsqu’un utilisateur appuie sur le bouton **[!UICONTROL Annuler]** d’une alerte ou d’un message en plein écran.

* **[!UICONTROL Engagement Rate]**, a calculated metric from Adobe Analytics and is the result of the number of click throughs divided by the number of impressions.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Si vous affichez des rapports pour un message push, le rapport ressemble à l’illustration suivante :

![message push](assets/report_message_push.png)

Le graphique de la partie supérieure affiche le nombre d’utilisateurs qui ont ouvert le message.

### Mesures des messages push

Voici la liste des mesures disponibles pour les messages push :

* **[!UICONTROL Heure]**

   Heure à laquelle le message a été transmis aux appareils à partir de Mobile Services.

* **[!UICONTROL État]**

   L’état du message et les états disponibles sont les suivants :

   * **[!UICONTROL Annulé]**
   * **[!UICONTROL Planifiée]**
   * **[!UICONTROL Exécution]**
   * **[!UICONTROL Exécuté]**

* **[!UICONTROL Published](Publié)**

   Nombre de jetons de périphérique envoyés avec succès à Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) pour envoyer le message aux périphériques des utilisateurs.

* **[!UICONTROL Échec]**

   Nombre de jetons de périphérique non envoyés à APNS/FCM. Quelques raisons possibles d'échec :

   * pushID non valide

   * The push platform (APNS, FCM, and so on) that was given to push to does not exist for the job's application. Par exemple, la plateforme peut collecter des jetons push iOS, mais aucun service APNS n’est configuré.

   * L’échec du message peut être dû à la configuration incorrecte du service push ou à l’indisponibilité du système Mobile Services.
   >[!IMPORTANT]
   >
   >Si vous constatez un nombre d’échecs inhabituellement élevé, vérifiez la configuration des services Push. Si les services Push semblent configurés correctement, contactez le service clientèle d’Adobe.

* **[!UICONTROL Bloqué sur liste noire]**

   Nombre de jetons de périphérique qui ne sont plus valides pour être envoyés à APNS ou FCM. Cela signifie habituellement que l’application a été désinstallée du périphérique ou que l’utilisateur a modifié ses paramètres de réception des messages. Le moment où les jetons sont considérés comme étant sur liste noire dépend selon qu’il s’agit d’une plateforme Android ou iOS. Les jetons Android sont immédiatement pris en compte comme figurant dans la liste noire. Les jetons iOS apparaissent tout d’abord comme étant publiés, mais selon le retour d’APNS, ils apparaissent ensuite comme étant sur liste noire dans les messages suivants.

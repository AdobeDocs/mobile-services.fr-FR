---
description: Vous pouvez utiliser ces informations pour configurer les options des services push sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Configuration de la messagerie push
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Configuration de la messagerie push {#configure-push-messaging}

Vous pouvez utiliser ces informations pour configurer les options des services push sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.

Avant de configurer la messagerie push, effectuez les tâches préalables requises dans [Conditions préalables requises pour activer la messagerie push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Considérations sur les suites de rapports**

   Vous pouvez configurer une application de boutique d’applications pour Apple et une application pour Google dans chaque suite de rapports. Si vous avez besoin d’applications supplémentaires, par exemple, une pour un environnement de production et une pour un environnement de développement, configurez une nouvelle application de boutique d’applications et une nouvelle suite de rapports pour chaque environnement.

>[!IMPORTANT]
>
>Vous ne pouvez pas déplacer votre application vers une nouvelle suite de rapports. Si vous migrez vers une nouvelle suite de rapports, votre configuration push peut devenir défaillante et les messages peuvent ne pas être envoyés.

1. Renseignez les champs suivants sous **[!UICONTROL Services push]** :

   * Apple

      **[!UICONTROL Clé privée]**

      Recherchez et sélectionnez votre clé privée valide `.p12`, `.key`, ou `.pen`.

      >[!IMPORTANT]
      >Si le fichier que vous sélectionnez pour la saisie de la **[!UICONTROL clé privée]** contient également un certificat, il n’est pas nécessaire de spécifier ce dernier.

   * **[!UICONTROL Certificat]**

      Spécifiez un certificat valide. Cette information est requise uniquement si la saisie **[!UICONTROL clé privée]** ne contient **aucun** certificat. Pour plus d’informations sur l’obtention du certificat SSL et de la clé privée, voir [Configuration d’une application pour l’utilisation du service APNS ou FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Clé API]**

      Spécifier une clé API valide. Pour plus d’informations sur l’obtention de la clé d’API, voir [Configuration d’une application pour l’utilisation du service APNS ou FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Pour plus d’informations, voir les rubriques suivantes :

      * [Messagerie push dans Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Messagerie push dans iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

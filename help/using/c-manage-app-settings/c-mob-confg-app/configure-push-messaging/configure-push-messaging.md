---
description: Vous pouvez utiliser ces informations pour configurer les options des services push sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
keywords: mobile
seo-description: Vous pouvez utiliser ces informations pour configurer les options des services push sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
seo-title: Configuration de la messagerie push
solution: Marketing Cloud, Analytics
title: Configuration de la messagerie push
topic: Mesures
uuid: 6763858 d -6046-4 d 36-87 c 0-cf 3600 a 44 fb 1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

Vous pouvez utiliser ces informations pour vous aider à configurer les options de services Push sur la page Gérer les paramètres de l'application lors de la création d'une nouvelle application ou de la modification d'une application existante.

Avant de configurer la messagerie Push, effectuez les tâches préalables dans [Conditions préalables pour activer la messagerie Push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Étude de la suite de rapports**

   Vous pouvez configurer une application de la boutique d’applications pour Apple et une pour Google dans chaque suite de rapports. Si vous avez besoin d’applications supplémentaires, par exemple, une pour l’environnement de production et une pour l’environnement de développement, configurez une nouvelle application de la boutique d’applications et une nouvelle suite de rapports pour chaque environnement.

>[!IMPORTANT]
>
>Le déplacement de votre application vers une nouvelle suite de rapports n'est pas pris en charge. Si vous migrez vers une nouvelle suite de rapports, votre configuration push peut devenir défaillante et les messages peuvent ne pas être envoyés.

1. Type information in the following fields under **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL Clé privée]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL Certificat]**

      Spécifiez un certificat valide. Cette information est requise uniquement si la saisie **[!UICONTROL Clé privée]** ne contient **aucun** certificat. Pour plus d'informations sur l'obtention du certificat SSL et de la clé privée, voir [Configuration de l'application pour utiliser APNS ou FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Clé API]**

      Spécifier une clé API valide. Pour plus d'informations sur l'obtention de la clé d'API, voir [Configuration de l'application pour utiliser APNS ou FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Pour plus d’informations, voir les rubriques suivantes :

      * [Messagerie Push dans Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Messagerie Push dans ios](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

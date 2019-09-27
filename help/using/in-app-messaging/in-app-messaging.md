---
description: Créez et gérez les messages in-app et push, puis créez des rapports sur ces derniers.
keywords: mobile
seo-description: Créez et gérez les messages in-app et push, puis créez des rapports sur ces derniers.
seo-title: Messagerie
solution: Marketing Cloud,Analytics
title: Messagerie
topic: Mesures
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Messagerie {#messaging}

Vous pouvez créer, gérer et générer des rapports sur les messages in-app et push.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Pour plus d’informations sur l’utilisation de la messagerie Push et de la messagerie intégrée (in-app) avec les SDK Experience Platform, reportez-vous à la section [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) (Configuration de la messagerie Push) et [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging) (Configuration de la messagerie intégrée).

## Les messages in-app {#section_8984F4568BC24D32A87429FFCB5184A6}

Les messages in-app sont remis en temps réel aux utilisateurs, selon leurs actions et leurs caractéristiques. Les messages sont déclenchés à partir des données Analytics qui font déjà l’objet d’un suivi par le SDK.

Les types de messages suivants sont pris en charge :

* Personnalisés et à thème
* Plein écran
* Alertes natives
* Notifications locales

To help you understand how in-app messaging works, here is some additional information:

* In-app messages require SDK version 4.2 or later.
* You must specify who has Mobile App Admin rights.

   Ces droits permettent d’accéder aux liens d’acquisition et aux messages in-app. For more information, see Roles and permissions.[](/help/using/gs/c-mob-roles-and-permissions.md)
* Une fois un message approuvé, il est publié automatiquement dans l’application.
* Le SDK présente le message aux utilisateurs lorsque les paramètres du message (caractéristiques, déclencheur et planification) sont satisfaits.
* Les messages peuvent contenir du code HTML personnalisé ou une image, en utilisant une URL en ligne.

   Une image de sauvegarde ou alternative issue du lot de l’application peut également être spécifiée pour les messages déclenchés en mode hors ligne.
* Les messages actifs et terminés fournissent des rapports sur le nombre total de consultations, les taux de clics publicitaires, etc.
* Les modèles sont disponibles pour les messages personnalisés, ce qui vous permet de créer facilement votre propre message in-app.

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

Les messages push sont envoyés aux utilisateurs qui ont accepté de recevoir des notifications. Vous pouvez cibler ces messages push envoyés aux utilisateurs dans les segments d’Analytics ou des segments personnalisés. Vous pouvez utiliser des messages push pour remotiver des utilisateurs passifs ou transmettre des informations temporelles et géographiques précises, car les messages s’affichent en dehors de votre application.

Before you can configure push messaging, see Prerequisites to enable push messaging. [](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md) Après avoir accompli ces tâches, vous devez configurer la messagerie push dans les paramètres de votre application. For more information, see [Configure push messaging](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).

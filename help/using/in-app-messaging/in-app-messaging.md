---
description: Créez et gérez les messages in-app et push, puis créez des rapports sur ces derniers.
keywords: mobile
seo-description: Créez et gérez les messages in-app et push, puis créez des rapports sur ces derniers.
seo-title: Messagerie
solution: Experience Cloud,Analytics
title: Messagerie
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 82%

---


# Messagerie {#messaging}

Vous pouvez créer et gérer les messages in-app et push, puis créez des rapports sur ces derniers.

## Nouvelle version du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* To get started, go to [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Si vous utilisez les SDK Adobe Experience Platform Mobile avec Adobe Launch, vous **devez** également installer l’extension Adobe Analytics Mobile Services pour utiliser les fonctionnalités Adobe Mobile Services comme les liens Acquisition. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Pour plus d’informations sur l’utilisation de la messagerie Push et de la messagerie intégrée (in-app) avec les SDK Experience Platform, reportez-vous à la section [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) (Configuration de la messagerie Push) et [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging) (Configuration de la messagerie intégrée).

## Les messages in-app {#section_8984F4568BC24D32A87429FFCB5184A6}

Les messages in-app sont remis en temps réel aux utilisateurs, selon leurs actions et leurs caractéristiques. Les messages sont déclenchés à partir des données Analytics qui font déjà l’objet d’un suivi par le SDK.

Les types de message suivants sont pris en charge :

* Personnalisé et thématique
* Plein écran
* Alertes natives
* Notifications locales

Pour vous aider à comprendre le fonctionnement de la messagerie in-app, voici quelques informations supplémentaires :

* Les messages in-app requièrent le SDK version 4.2 ou ultérieure.
* Vous devez spécifier le détenteur des droits d’administrateur des applications mobiles.

   Ces droits donnent accès aux liens d’acquisition et aux messages in-app. Pour plus d’informations, voir [Rôles et autorisations](/help/using/gs/c-mob-roles-and-permissions.md).
* Une fois qu’un message est approuvé, il est publié automatiquement dans l’application.
* Le SDK présente le message aux utilisateurs lorsque les paramètres du message, tels que les caractéristiques, le déclencheur et la planification, sont satisfaits.
* Les messages peuvent contenir du code HTML personnalisé ou une image, à l’aide d’une URL en ligne.

   Une image de sauvegarde ou alternative issue du lot d’applications peut également être spécifiée pour les messages déclenchés hors ligne.
* Les messages actifs et terminés fournissent des rapports sur le nombre total de consultations, les taux de clics publicitaires, etc.
* Les modèles sont disponibles pour les messages personnalisés, ce qui vous permet de créer facilement votre propre message in-app.

## Messages push {#section_90555A55BCE7427A90B1577E14BEF51B}

Les messages push sont envoyés aux utilisateurs qui ont accepté de recevoir des notifications. Vous pouvez cibler ces messages push envoyés aux utilisateurs dans les segments d’Analytics ou des segments personnalisés. Vous pouvez utiliser des messages push pour remotiver des utilisateurs passifs ou transmettre des informations temporelles et géographiques précises, car les messages s’affichent en dehors de votre application.

Avant de pouvoir configurer la messagerie push, voir [Conditions préalables requises pour activer la messagerie push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Après avoir accompli ces tâches, vous devez configurer la messagerie push dans les paramètres de votre application. Pour plus d’informations, voir [Configuration de la messagerie push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).

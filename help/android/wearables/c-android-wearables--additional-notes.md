---
description: Voici quelques informations pour vous aider à configurer l'extension Android, qui vous permet de collecter des données depuis votre application Android Wearable.
seo-description: Voici quelques informations pour vous aider à configurer l'extension Android, qui vous permet de collecter des données depuis votre application Android Wearable.
seo-title: 'Android Wearables : Remarques supplémentaires'
solution: Experience Cloud,Analytics
title: 'Android Wearables : Remarques supplémentaires'
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 51%

---


# Android Wearables : Remarques supplémentaires{#android-wearables-additional-notes}

Voici quelques informations pour vous aider à configurer l&#39;extension Android, qui vous permet de collecter des données depuis votre application Android Wearable.

* L&#39;Adobe Mobile Android Wearables Extension requiert Android version 4.4 (KitKat) ou ultérieure.
* Il existe une valeur de contexte supplémentaire, `A.RunMode`, qui a été ajoutée pour indiquer si les données viennent de l’application ou de l’extension.

   * `RunMode` = `Application`

      L’accès provient de l’application pour portables.

   * `RunMode` = `Extension`

      L’accès provient de l’application portable.

* Le SDK synchronise automatiquement l’état `aid`/`vid`/`visitor`/`service id` depuis l’application pour portables vers l’application pour wearables. Il ne convient, par conséquent, pas d’appeler `privacy`/`setPrivacyStatus`/`setUserIdentifier`/`idSync` depuis l’application pour wearables.
* [Les messagesin-app](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) et [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sont désactivés pour l’application portable.


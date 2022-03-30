---
description: Voici quelques informations pour vous aider à configurer l’extension Android, qui vous permet de collecter des données depuis votre application Android Wearable.
solution: Experience Cloud Services,Analytics
title: 'Android Wearables : Remarques supplémentaires'
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Android Wearables : Remarques supplémentaires {#android-wearables-additional-notes}

Voici quelques informations pour vous aider à configurer l’extension Android, qui vous permet de collecter des données depuis votre application Android Wearable.

* L’extension Adobe Mobile Android Wearables requiert Android version 4.4 (KitKat) ou ultérieure.
* Il existe une valeur de contexte supplémentaire, `A.RunMode`, qui a été ajoutée pour indiquer si les données viennent de l’application ou de l’extension.

   * `RunMode` = `Application`

      L’accès provient de l’application pour portables.

   * `RunMode` = `Extension`

      L’accès provient de l’application portable.

* Le SDK synchronise automatiquement l’état `aid`/`vid`/`visitor`/`service id` depuis l’application pour portables vers l’application pour wearables. Il ne convient, par conséquent, pas d’appeler `privacy`/`setPrivacyStatus`/`setUserIdentifier`/`idSync` depuis l’application pour wearables.
* [Les messagesin-app](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) et [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sont désactivés pour l’application portable.

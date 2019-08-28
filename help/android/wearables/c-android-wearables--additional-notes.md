---
description: Informations destinées à vous aider à configurer l’extension Android qui permet de collecter des données depuis l’application Android Wearable.
seo-description: Informations destinées à vous aider à configurer l’extension Android qui permet de collecter des données depuis l’application Android Wearable.
seo-title: Android Wearables - Remarques supplémentaires
solution: Marketing Cloud, Analytics
title: Android Wearables - Remarques supplémentaires
topic: Développeur et mise en œuvre
uuid: 3 bcf 352 b -4 d 46-4 ab 3-81 ec-c 27 e 86 fe 9 be 3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

Informations destinées à vous aider à configurer l’extension Android qui permet de collecter des données depuis l’application Android Wearable.

* L’extension Android Wearables pour Adobe Mobile requiert Android version 4.4 (KitKat) ou supérieure.
* Il existe une valeur de contexte supplémentaire, `A.RunMode`, qui a été ajoutée pour indiquer si les données viennent de l’application ou de l’extension.

   * `RunMode` = `Application`

      L'accès provient de l'application portable.

   * `RunMode` = `Extension`

      L'accès provient de l'application Wearable.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [Les messages in-app](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md)et [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sont désactivés pour l'application wearable.


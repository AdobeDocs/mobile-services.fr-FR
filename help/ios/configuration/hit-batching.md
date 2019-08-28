---
description: Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.
seo-description: Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.
seo-title: Traitement par lot des accès
solution: Marketing Cloud, Analytics
title: Traitement par lot des accès
topic: Développeur et mise en œuvre
uuid: 3 dda 7372-0695-4 cb 7-b 779-6 abca 2 d 6 e 0 d 9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Traitement par lot des accès {#hit-batching}

Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.

>[!IMPORTANT]
>
>Le traitement par lot des accès nécessite le SDK version 4.1 ou ultérieure.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Lorsque la valeur définie est supérieure à 0, le SDK place les accès en file d’attente tant que leur nombre est inférieur ou égal à *`batchLimit`*. Une fois ce seuil atteint, tous les accès de la file d’attente sont envoyés.

Les méthodes suivantes sont utilisées avec le traitement par lot des accès :

* `trackingGetQueueSize()` renvoie un `NSUInteger` correspondant au nombre d’accès actuellement placés en attente.
* `trackingSendQueuedHits()` force la bibliothèque à envoyer tous les accès de la file d’attente, peu importe le nombre d’accès déjà en file d’attente.
* `trackingClearQueue()` efface tous les accès de la file d’attente sans les envoyer.

>[!CAUTION]
>
>Le suivi hors ligne doit être activé pour utiliser le traitement par lot des accès.


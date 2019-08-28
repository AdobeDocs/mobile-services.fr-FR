---
description: Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.
keywords: android ; library ; mobile ; sdk
seo-description: Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.
seo-title: Traitement par lot des accès
solution: Marketing Cloud, Analytics
title: Traitement par lot des accès
topic: Développeur et mise en œuvre
uuid: ada 35 be 3-242 b -4 b 2 b-a 828-9 bf 998 dd 58 b 5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Traitement par lot des accès {#hit-batching}

Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.

>[!IMPORTANT]
>
>Pour utiliser le traitement par lot des accès, vous **devez** activer le suivi hors ligne et disposer du SDK version 4.1 ou ultérieure

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. Une fois ce seuil atteint, tous les accès de la file d’attente sont envoyés.

Les méthodes suivantes sont utilisées avec le traitement par lot des accès :

* `Analytics.getQueueSize` renvoie une valeur `long` indiquant le nombre d’accès actuellement dans la file d’attente du traitement par lot des accès.

* `Analytics.sendQueuedHits` force la bibliothèque à envoyer tous les accès de la file d’attente, peu importe le nombre d’accès déjà en file d’attente.
* `Analytics.clearQueue` efface tous les accès de la file d’attente sans les envoyer.

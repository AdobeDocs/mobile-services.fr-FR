---
description: Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.
keywords: android;library;mobile;sdk
seo-description: Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.
seo-title: Traitement par lot des accès
solution: Experience Cloud,Analytics
title: Traitement par lot des accès
topic: Développeur et mise en œuvre
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Traitement par lot des accès {#hit-batching}

Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.

>[!IMPORTANT]
>
>Pour utiliser le traitement par lot des accès, vous **devez** activer le suivi hors ligne et disposer du SDK version 4.1 ou ultérieure

Pour activer le traitement par lot des accès, mettez à jour le fichier `ADBMobileConfig.json` et indiquez une valeur pour `batchLimit` :

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Lorsque la valeur est définie sur un nombre supérieur à 0, le SDK place les accès en file d’attente tant que leur nombre est inférieur ou égal à la valeur *`batchLimit`*. Une fois ce seuil atteint, tous les accès de la file d’attente sont envoyés.

Les méthodes suivantes sont utilisées avec le traitement par lot des accès :

* `Analytics.getQueueSize` renvoie une valeur `long` indiquant le nombre d’accès actuellement dans la file d’attente du traitement par lot des accès.

* `Analytics.sendQueuedHits` force la bibliothèque à envoyer tous les accès de la file d’attente, peu importe le nombre d’accès déjà en file d’attente.
* `Analytics.clearQueue` efface tous les accès de la file d’attente sans les envoyer.

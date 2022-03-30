---
description: Le traitement par lot des accès permet aux applications de différer l’envoi d’accès jusqu’à ce que le nombre d’accès dans la file d’attente dépasse la limite configurée.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Traitement par lot des accès
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

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

Lorsque la valeur est définie sur un nombre supérieur à 0, le SDK place les accès en file d’attente tant que leur nombre est inférieur ou égal à la valeur *`batchLimit`*. Une fois ce seuil dépassé, tous les accès de la file d’attente sont envoyés.

Les méthodes suivantes sont utilisées avec le traitement par lot des accès :

* `Analytics.getQueueSize` renvoie une valeur `long` indiquant le nombre d’accès actuellement dans la file d’attente du traitement par lot des accès.

* `Analytics.sendQueuedHits` force la bibliothèque à envoyer tous les accès de la file d’attente, peu importe le nombre d’accès déjà en file d’attente.
* `Analytics.clearQueue` efface tous les accès de la file d’attente sans les envoyer.

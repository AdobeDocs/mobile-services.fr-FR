---
description: Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.
seo-description: Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.
seo-title: Traitement par lot des accès
solution: Experience Cloud,Analytics
title: Traitement par lot des accès
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 100%

---

# Traitement par lot des accès {#hit-batching}

Le traitement par lot des accès permet aux applications dont le suivi hors ligne est activé de bloquer l’envoi d’accès tant que le nombre d’accès de la file d’attente n’a pas dépassé une limite configurable.

>[!IMPORTANT]
>
>Le traitement par lot des accès requiert le SDK version 4.1 ou supérieure.

Pour activer le traitement par lot des accès, mettez à jour le fichier `ADBMobileConfig.json` et indiquez une valeur pour `batchLimit` :

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Lorsque la valeur définie est supérieure à 0, le SDK place les accès en file d’attente tant que leur nombre est inférieur ou égal à *`batchLimit`*. Une fois ce seuil dépassé, tous les accès de la file d’attente sont envoyés.

Les méthodes suivantes sont utilisées avec le traitement par lot des accès :

* `trackingGetQueueSize()` renvoie un `NSUInteger` correspondant au nombre d’accès actuellement placés en attente.
* `trackingSendQueuedHits()` force la bibliothèque à envoyer tous les accès de la file d’attente, peu importe le nombre d’accès déjà en file d’attente.
* `trackingClearQueue()` efface tous les accès de la file d’attente sans les envoyer.

>[!CAUTION]
>
>Le suivi hors ligne doit être activé pour pouvoir utiliser le traitement par lot des accès.

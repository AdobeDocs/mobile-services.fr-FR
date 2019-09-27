---
description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel au serveur.
seo-description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel au serveur.
seo-title: Sérialisation d’événements
solution: Marketing Cloud,Analytics
title: Sérialisation d’événements
topic: Développeur et mise en œuvre
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Sérialisation d’événements {#event-serialization}

La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre des données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.

```js
cdata["&&events"] = "event1:12341234";
```

Par exemple :

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```


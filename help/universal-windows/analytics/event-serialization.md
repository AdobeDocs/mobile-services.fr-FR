---
description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.
seo-description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.
seo-title: Sérialisation d’événements
solution: Experience Cloud,Analytics
title: Sérialisation d’événements
topic-fix: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# Sérialisation d’événements {#event-serialization}

La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.

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

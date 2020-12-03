---
description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.
seo-description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir des événements sérialisés directement sur l’appel au serveur.
seo-title: Sérialisation d’événements
solution: Experience Cloud,Analytics
title: Sérialisation d’événements
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---


# Sérialisation d’événements{#event-serialization}

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


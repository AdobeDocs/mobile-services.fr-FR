---
description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel au serveur.
seo-description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel au serveur.
seo-title: Sérialisation d’événements
solution: Marketing Cloud, Analytics
title: Sérialisation d’événements
topic: Développeur et mise en œuvre
uuid: a 5966 d 05-e 218-446 f -9 f 19-8664 a 84 b 74 cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# Sérialisation d’événements{#event-serialization}

La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement sur l'appel serveur.

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


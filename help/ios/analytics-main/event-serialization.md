---
description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés sur l’appel au serveur.
seo-description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés sur l’appel au serveur.
seo-title: Sérialisation d’événements
solution: Experience Cloud,Analytics
title: Sérialisation d’événements
topic-fix: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
exl-id: c34331a4-bfe2-4955-807b-92a3303f8d81
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 100%

---

# Sérialisation d’événements {#event-serialization}

La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés sur l’appel au serveur.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Par exemple :

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

---
description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.
seo-description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.
seo-title: Sérialisation d’événements
solution: Marketing Cloud, Analytics
title: Sérialisation d’événements
topic: Développeur et mise en œuvre
uuid: 19 a 27 df 4-0998-403 d -800 c -26 ff 61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Sérialisation d’événements {#event-serialization}

La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.

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


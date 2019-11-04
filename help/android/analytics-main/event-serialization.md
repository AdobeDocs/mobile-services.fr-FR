---
description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.
keywords: android;library;mobile;sdk
seo-description: La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.
seo-title: Sérialisation d’événements
solution: Experience Cloud,Analytics
title: Sérialisation d’événements
topic: Développeur et mise en œuvre
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Sérialisation d’événements {#event-serialization}

La sérialisation d’événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés directement dans l’appel de serveur.

```java
cdata.put("&&events", "event1:12341234");
```

Par exemple :

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```


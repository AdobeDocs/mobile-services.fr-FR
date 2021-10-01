---
description: La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés sur l’appel au serveur.
keywords: android;library;mobile;sdk
solution: Experience Cloud,Analytics
title: Sérialisation d’événements
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 100%

---

# Sérialisation d’événements {#event-serialization}

La sérialisation des événements n’est pas prise en charge par les règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les événements sérialisés sur l’appel au serveur.

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

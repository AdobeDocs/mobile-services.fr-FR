---
description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-title: Remplacement du chemin du fichier de configuration JSON ADBMobile
solution: Experience Cloud,Analytics
title: Remplacement du chemin du fichier de configuration JSON ADBMobile
topic: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%

---


# Remplacement du chemin du fichier de configuration JSON ADBMobile{#override-the-adbmobile-json-config-path}

Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.

La méthode `Config.overrideConfigStream(configInput)` permet de spécifier le chemin d’accès à un autre fichier de configuration `ADBMobile.json` lors du démarrage de l’application. Cette méthode doit être appelée avant tout autre appel du SDK Experience Cloud (avant `Config.collectLifecycleData()` ), généralement dans la méthode `onCreate` de la première activité chargée.

L’appel de cette méthode avec un autre chemin d’accès entraîne un remplacement unique du fichier de configuration, jusqu’à la fermeture de l’application.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```


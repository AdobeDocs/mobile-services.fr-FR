---
description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-title: Remplacement du chemin du fichier de configuration JSON ADBMobile
solution: Marketing Cloud, Analytics
title: Remplacement du chemin du fichier de configuration JSON ADBMobile
topic: Développeur et mise en œuvre
uuid: 6872 a 5 d 7-0 c 5 a -4 fdc-b 7 bf-ad 1534763 a 6 a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.

The `Config.overrideConfigStream(configInput)` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

L’appel de cette méthode avec un autre chemin d’accès entraîne un remplacement unique du fichier de configuration, jusqu’à la fermeture de l’application.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

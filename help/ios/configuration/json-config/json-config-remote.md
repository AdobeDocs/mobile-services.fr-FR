---
description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-title: Remplacement du chemin de configuration ADBMobile JSON
solution: Marketing Cloud,Analytics
title: Override the ADBMobile JSON config path
topic: Développeur et mise en œuvre
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Cette méthode doit être appelée dans la méthode `applicationDidFinishLaunchingWithOptions` et l’appel doit avoir lieu avant tout autre appel du SDK Experience Cloud, notamment `collectLifecycleData`.

Lorsque vous appelez cette méthode avec un chemin différent, un remplacement unique du fichier de configuration se produit jusqu’à la fermeture de l’application.

Par exemple :

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```


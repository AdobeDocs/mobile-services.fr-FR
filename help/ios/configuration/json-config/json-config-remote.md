---
description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-title: Remplacement du chemin du fichier de configuration JSON ADBMobile
solution: Experience Cloud,Analytics
title: Remplacement du chemin du fichier de configuration JSON ADBMobile
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '120'
ht-degree: 100%

---


# Remplacement du chemin du fichier de configuration JSON ADBMobile {#override-the-adbmobile-json-config-path}

Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.

La méthode `ADBMobile overrideConfigPath:filePath` permet de spécifier le chemin d’accès à un autre fichier de configuration `ADBMobile.json` lors du démarrage de l’application. Cette méthode doit être appelée dans la méthode `applicationDidFinishLaunchingWithOptions` et l’appel doit avoir lieu avant tout autre appel du SDK Experience Cloud, notamment `collectLifecycleData`.

L’appel de cette méthode avec un autre chemin d’accès entraîne un remplacement unique du fichier de configuration, jusqu’à la fermeture de l’application.

Par exemple :

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```


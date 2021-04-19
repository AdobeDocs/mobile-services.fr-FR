---
description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-description: Vous pouvez charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application.
seo-title: Remplacement du chemin du fichier de configuration JSON ADBMobile
solution: Experience Cloud,Analytics
title: Remplacement du chemin du fichier de configuration JSON ADBMobile
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
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

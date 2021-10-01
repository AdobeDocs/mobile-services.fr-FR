---
description: Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.
solution: Experience Cloud,Analytics
title: Intégration de Swift
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Intégration de Swift {#swift-integration}

Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.

Pour plus d’informations, voir [Interopérabilité des langues](https://developer.apple.com/documentation/swift#2984801.html).

Par exemple, en utilisant la méthode bridging-header comme décrit dans la documentation, vous pouvez importer le fichier d’en-tête du SDK iOS Adobe Mobile :

```
#import "ADBMobile.h"
```

Pour accéder aux méthodes du SDK dans vos fichiers Swift, utilisez le format suivant :

```
ADBMobile.{methodname}
```

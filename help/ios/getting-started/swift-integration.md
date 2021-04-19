---
description: Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.
seo-description: Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.
seo-title: Intégration de Swift
solution: Experience Cloud,Analytics
title: Intégration de Swift
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---

# Intégration de Swift {#swift-integration}

Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.

Pour plus d’informations, voir [Interopérabilité des langues](https://developer.apple.com/documentation/swift#2984801.html).

Par exemple, en utilisant la méthode bridging-header comme décrit dans la documentation, vous pouvez importer le fichier d’en-tête du SDK iOS Adobe Mobile :

```
#import “ADBMobile.h”
```

Pour accéder aux méthodes du SDK dans vos fichiers Swift, utilisez le format suivant :

```
ADBMobile.{methodname}
```

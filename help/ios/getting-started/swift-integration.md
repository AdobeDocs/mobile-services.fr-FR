---
description: Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.
seo-description: Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.
seo-title: Intégration de Swift
solution: Marketing Cloud,Analytics
title: Intégration de Swift
topic: Développeur et mise en œuvre
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

Il est possible d’intégrer un SDK iOS Adobe Mobile à un projet Swift en toute transparence à l’aide de la fonctionnalité « Mix and Match » de la bibliothèque de développement iOS.

For more information, see [Language Interoperability](https://developer.apple.com/documentation/swift#2984801.html).

Par exemple, en utilisant la méthode bridging-header décrite dans la documentation, vous pouvez importer le fichier d’en-tête du SDK iOS Adobe Mobile :

```
#import “ADBMobile.h”
```

Utilisez le format suivant pour accéder aux méthodes à partir du SDK dans vos fichiers Swift :

```
ADBMobile.{methodname}
```


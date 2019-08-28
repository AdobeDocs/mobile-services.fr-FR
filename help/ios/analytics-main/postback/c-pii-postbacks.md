---
description: Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.
seo-description: Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.
seo-title: Postbacks de type PII
title: Postbacks de type PII
uuid: 08 f 76 a 52-75 dd -4 fc 1-b 4 cc -4 f 5 eef 93 d 0 f 7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.

Si vous souhaitez utiliser le SDK Adobe pour recueillir des informations d’identification personnelles, vous devez envoyer un appel PII de suivi. Bien que l’utilisation de cet appel active la collecte des données PII, le SDK n’envoie pas automatiquement les données vers un point de terminaison Adobe. Un postback de type PII doit être configuré avec le point de terminaison approprié.

>[!TIP]
>
>Un point de fin prenant en charge HTTPS est nécessaire pour utiliser le type de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Lorsque vous êtes prêt à capturer les informations d’identification personnelles, appelez `trackPII` pour envoyer un accès pour cette action, événement ou affichage :

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```


---
description: Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.
seo-description: Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.
seo-title: Postbacks de type PII
title: Postbacks de type PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.

Si vous souhaitez utiliser le SDK Adobe pour recueillir des informations d’identification personnelles, vous devez envoyer un appel PII de suivi. Bien que l’utilisation de cet appel active la collecte des données PII, le SDK n’envoie pas automatiquement les données vers un point de terminaison Adobe. Un postback de type PII doit être configuré avec le point de terminaison approprié.

>[!TIP]
>
>Un point de fin prenant en charge HTTPS est nécessaire pour utiliser le type de postback d’informations d’identification personnelle.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Add [the library to your project and implement lifecycle.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* IntelliJ IDEA ou Eclipse dans l’implémentation et le cycle de vie [](/help/android/getting-started/dev-qs.md)principaux.

1. Importez la bibliothèque :

   ```java
   #import "ADBMobile.h"
   ```

1. Lorsque vous êtes prêt à capturer les informations d’identification personnelles, appelez `trackPII` pour envoyer un accès pour cette action, événement ou affichage :

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```


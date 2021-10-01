---
description: Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.
title: Postbacks de type PII
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# Postbacks de type PII {#pii-postbacks}

Vous pouvez utiliser le SDK Adobe pour collecter des informations d’identification personnelle (PII) et les envoyer à un point de terminaison tiers.

Si vous souhaitez utiliser le SDK Adobe pour collecter des informations d’identification personnelle, vous devez envoyer un appel track PII. Bien que l’utilisation de cet appel permette la collecte de données d’identification personnelle, le SDK n’envoie pas automatiquement les données à un point de terminaison d’Adobe. Un postback de type PII doit être configuré avec le point de terminaison approprié.

>[!TIP]
>
>Un point de terminaison qui prend en charge HTTPS est requis pour utiliser le postback de type PII.

## Suivi des postbacks de type PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Lorsque vous êtes prêt à capturer les informations d’identification personnelles, appelez `trackPII` pour envoyer un accès pour cette action, événement ou affichage :

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

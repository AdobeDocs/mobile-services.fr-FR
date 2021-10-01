---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
title: Target Preview sous iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# Target Preview sous iOS{#target-preview-on-ios}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

Pour plus d’informations sur la configuration et l’utilisation de Target Preview, voir [Aperçu de Target Mobile](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) dans la documentation d’Adobe Target.

>[!IMPORTANT]
>
>Pour utiliser Target Preview, vous avez besoin du SDK version 4.14.0 ou ultérieure.

## Méthode Target Preview

* **setPreviewRestartDeeplink**

   Définit un lien profond d’application qui sera déclenché lorsque les sélections de prévisualisation seront appliquées en mode Prévisualisation.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```

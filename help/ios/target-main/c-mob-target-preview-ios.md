---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-title: Target Preview sous iOS
title: Target Preview sous iOS
uuid: d 92867 a 4-0569-4732-a 928-28 f 9 e 2 f 8 b 21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Target Preview sous iOS{#target-preview-on-ios}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Pour utiliser l'aperçu de Target, vous avez besoin de SDK version 4.14.0 ou ultérieure.

## Méthode d'aperçu cible

* **setPreviewRestartDeeplink**

   Définit un lien profond vers des applications qui sera déclenché lorsque les sélections d’aperçu sont appliquées en mode Aperçu.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```

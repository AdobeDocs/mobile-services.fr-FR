---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-title: Target Preview sous iOS
title: Target Preview sous iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '141'
ht-degree: 100%

---


# Target Preview sous iOS {#target-preview-on-ios}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

Pour plus d’informations sur la configuration et l’utilisation de Target Preview, voir [Aperçu de Target Mobile](https://docs.adobe.com/content/help/fr-FR/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```

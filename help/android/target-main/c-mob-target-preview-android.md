---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-title: Target Preview sous Android
title: Target Preview sous Android
uuid: f 3 c 82 d 64-009 c -4929-a 5 e 6-3677 b 2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Target Preview sous Android {#target-preview-on-android}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

Pour plus d’informations sur la configuration et l’utilisation de Target Preview, aller à [Aperçu de Target Mobile](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Pour utiliser l'aperçu de Target, vous avez besoin de SDK version 4.14.0 ou ultérieure.

* **setPreviewRestartDeeplink**

   Définit un lien profond vers des applications qui sera déclenché lorsque les sélections d’aperçu sont appliquées en mode Aperçu.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```


---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
seo-title: Target Preview sous Android
title: Target Preview sous Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: ht
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Target Preview sous Android {#target-preview-on-android}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

Pour plus d’informations sur la configuration et l’utilisation de Target Preview, aller à [Aperçu de Target Mobile](https://docs.adobe.com/content/help/fr-FR/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Pour utiliser Target Preview, vous avez besoin du SDK version 4.14.0 ou ultérieure.

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


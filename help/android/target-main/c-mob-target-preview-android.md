---
description: Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.
title: Target Preview sous Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Target Preview sous Android {#target-preview-on-android}

Target Preview permet d’effectuer facilement un contrôle qualité de bout en bout des activités Target et de prévisualiser ces dernières sur votre appareil.

Pour plus d’informations sur la configuration et l’utilisation de Target Preview, voir [Target Mobile Preview](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) dans le guide d’utilisation d’Adobe Target.

>[!IMPORTANT]
>
>Pour utiliser Target Preview, vous avez besoin du SDK version 4.14.0 ou ultérieure.

* **setPreviewRestartDeeplink**

   Définit un lien profond d’application qui sera déclenché lorsque les sélections de prévisualisation seront appliquées en mode Prévisualisation.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```

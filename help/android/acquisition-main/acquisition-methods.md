---
description: 'Les méthodes d''acquisition suivantes sont fournies par la bibliothèque Android. '
keywords: android ; library ; mobile ; sdk
seo-description: 'Les méthodes d''acquisition suivantes sont fournies par la bibliothèque Android. '
seo-title: Méthodes d’acquisition
solution: Marketing Cloud, Analytics
title: Méthodes d’acquisition
topic: Développeur et mise en œuvre
uuid: 22 ec 432 f-e 7 ae -4 e 89-be 07-26206 bbeacf 8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

La méthode Acquisition suivante est fournie par la bibliothèque Android :

* **campaignStartForApp**

   Permet aux développeurs de lancer une campagne d’acquisition d’applications, comme si l’utilisateur avait cliqué sur un lien. Ceci s’avère utile pour créer des liens d’acquisition manuels et pour gérer vous-même les redirections de boutiques d’applications.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```

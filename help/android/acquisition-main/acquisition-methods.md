---
description: 'Les méthodes d’acquisition suivantes sont fournies par la bibliothèque Android : '
keywords: android;library;mobile;sdk
solution: Experience Cloud,Analytics
title: Méthodes d’acquisition
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 100%

---

# Méthodes d’acquisition{#acquisition-methods}

La méthode d’acquisition suivante est fournie par la bibliothèque Android :

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

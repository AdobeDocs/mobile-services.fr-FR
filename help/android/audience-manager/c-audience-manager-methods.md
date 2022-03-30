---
description: Liste des méthodes Audience Manager fournies par la bibliothèque Android.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Méthodes Audience Manager
topic-fix: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
exl-id: 707b40b8-e56e-4c26-8b59-87c5d71cad0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 100%

---

# Méthodes Audience Manager{#audience-manager-methods}

Liste des méthodes Audience Manager fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform. Un préfixe est attribué aux méthodes selon la solution. Par exemple, les méthodes d’Experience Cloud ID sont affectées du préfixe `audience manager`.

Si Audience Manager est configuré dans le fichier JSON, un signal qui contient des mesures de cycle de vie est envoyé avec l’accès de cycle de vie.

* **getVisitorProfile**

   Renvoie le dernier profil du visiteur obtenu ou renvoie `null` lorsqu’aucun signal n’a été envoyé. Le profil du visiteur est enregistré dans `SharedPreferences` pour un accès facile à l’échelle de plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Renvoie le DPID en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void getDpid(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Renvoie le DPUUID en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void getDpuuid(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Définit le DPID et le DPUUID. Ces valeurs sont envoyées avec chaque signal.

   Si la valeur DPUUID transmise à cette méthode contient des caractères qui ne sont pas sécurisés contre les URL, les clients doivent coder le paramètre avant de le transmettre au SDK.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Envoie à la gestion de l’audience un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```

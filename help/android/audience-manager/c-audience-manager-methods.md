---
description: Liste des méthodes Audience Manager fournies par la bibliothèque Android.
keywords: android ; library ; mobile ; sdk
seo-description: Liste des méthodes Audience Manager fournies par la bibliothèque Android.
seo-title: Méthodes Audience Manager
solution: Marketing Cloud, Analytics
title: Méthodes Audience Manager
topic: Développeur et mise en œuvre
uuid: 2 f 6 e 4664-1306-41 d 4-9 fa 7-e 3 a 99 f 1 df 4 ab
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

Liste des méthodes Audience Manager fournies par la bibliothèque Android.

Le kit SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager et le service d'identité Adobe Experience Platform. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

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

   Si la valeur DPUUID transmise à cette méthode contient des caractères qui ne sont pas compatibles avec l'URL, les clients doivent coder le paramètre avant de le transmettre au SDK.

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

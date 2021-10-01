---
description: Liste des méthodes Adobe Target fournies par la bibliothèque Android.
keywords: android;library;mobile;sdk
solution: Experience Cloud,Analytics
title: Méthodes Target pour Android
topic-fix: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
exl-id: 0c7a6718-d078-4a2b-a2c9-d5cd50263939
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 95%

---

# Méthodes Target pour Android{#target-methods}

Liste des méthodes Adobe Target fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform. Un préfixe est attribué aux méthodes selon la solution. Par exemple, les méthodes d’Experience Cloud ID sont affectées du préfixe `target`.

>[!TIP]
>
>[Les mesures de cycle de vie](/help/android/metrics.md) sont envoyées sous la forme de paramètres à chaque chargement de mbox.

## Référence de classe : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Propriétés :**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Constantes de chaîne**

>[!TIP]
>
>Les constantes suivantes facilitent la définition des clés pour les paramètres personnalisés.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* Si vous utilisez un SDK **antérieur** à la version 4.14.0, voir [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) pour les restrictions des paramètres.
>
>* Si vous utilisez un SDK 4.14.0 **ou version supérieure**, voir [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) pour les restrictions des paramètres.


* **loadRequest**

   Envoie request au serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un bloc callback.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Envoie request au serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un bloc callback.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put("profile-parameter-key", "profile-parameter-value"); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put("order-parameter-key", "order-parameter-value");
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put("mbox-parameter-key", "mbox-parameter-value"); 
      Target.loadRequest("mboxName", "defaultContent", profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d("Target Content", item); 
          }
      });
      ```

* **loadRequest**

   Envoie une demande au serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un TargetCallback.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Renvoie :** S/O

   * **Paramètres :**

      Voici les paramètres pour cette méthode :

      * **name**

         Nom de la mbox/l’emplacement Target que vous voulez récupérer.

         * **Type :** String
      * **defaultContent**

         Valeur renvoyée dans le rappel si le serveur Target n’est pas accessible ou si l’utilisateur n’est pas admissible pour la campagne.

         * **Type :** String
      * **profileParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;profileParameters&quot; dans la demande à Target.

         * **Type :** Map `<String, Object>`
      * **orderParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;order&quot; dans la demande à Target.

         * **Type :** Map `<String, Object>`
      * **mboxParameters**

         Les valeurs de ce dictionnaire seront transférées dans la requête à Target.

         * **Type :** Map `<String, Object>`
      * **requestLocationParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;requestLocation&quot; dans la demande à Target.

         * **Type :** Map `<String, Object>`
      * **callback**

         Cette méthode est appelée avec le contenu de l’offre depuis le serveur Target. Si le serveur Target n’est pas accessible ou si l’utilisateur n’est pas admissible pour la campagne, la valeur defaultContent est renvoyée.

         * **Type :** TargetCallback `<String>`
   * Voici un exemple de code pour cette méthode :

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put("profile-parameter-key", "profile-parameter-value"); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put("order-parameter-key", "order-parameter-value"); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put("mbox-parameter-key", "mbox-parameter-value"); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put("request-location-parameter-key", "request-location-parameter-value"); 
      
      Target.loadRequest("mboxName", "defaultContent", profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d("Target Content", item);
         } 
      });
      ```

      Pour plus d’informations sur l’API Target sous-jacente, voir [Chargement de requêtes Target](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target/target-api-reference-deprecated#load-target-requests) dans la référence de l’API Target.








* **createOrder&#x200B;ConfirmRequest**

   Crée un objet TargetLocationRequest avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Crée un objet TargetLocationRequest avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Efface les cookies de ciblage de l’application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void clearCookies();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Renvoie l’ID de PC.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String getPcID();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Renvoie l’ID de session.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String getSessionID();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Définit l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.setThirdPartyID("third-party-id");
      ```

* **getThirdPartyID**

   Renvoie l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String getThirdPartyID();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```

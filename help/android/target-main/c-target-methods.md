---
description: Liste des méthodes Adobe Target fournies par la bibliothèque Android.
keywords: android ; library ; mobile ; sdk
seo-description: Liste des méthodes Adobe Target fournies par la bibliothèque Android.
seo-title: Méthodes Target pour Android
solution: Marketing Cloud, Analytics
title: Méthodes Target pour Android
topic: Développeur et mise en œuvre
uuid: 8 e 9808 b 2-ba 80-4646-ba 05-8 e 62 d 4 fde 065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Méthodes Target pour Android{#target-methods}

Liste des méthodes Adobe Target fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager et le service d'identité Adobe Experience Platform. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[Les mesures de cycle de vie](/help/android/metrics.md) sont envoyées sous la forme de paramètres à chaque chargement de mbox.

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Propriétés :**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Constantes de chaîne**

>[!TIP]
>
>Les constantes suivantes sont simplifiées : de - utilisées lorsque vous définissez des clés pour les paramètres personnalisés.

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
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


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
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
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

      Voici les paramètres de cette méthode :

      * **name**

         Nom de la mbox/l’emplacement Target que vous voulez récupérer.

         * **Type :** Chaîne
      * **defaultContent**

         Valeur renvoyée dans le rappel si le serveur Target n’est pas accessible ou si l’utilisateur n’est pas admissible pour la campagne.

         * **Type :** Chaîne
      * **profileParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet "profileParameters" dans la demande à Target.

         * **Type :** Carte `<String, Object>`
      * **orderParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet "order" dans la demande à Target.

         * **Type :** Carte `<String, Object>`
      * **mboxParameters**

         Les valeurs de ce dictionnaire seront envoyées à Target.

         * **Type :** Carte `<String, Object>`
      * **requestLocationParameters**

         Les valeurs de ce dictionnaire seront placées dans l’objet "requestLocation" dans la demande à Target.

         * **Type :** Carte `<String, Object>`
      * **callback**

         Cette méthode est appelée avec le contenu de l’offre depuis le serveur Target. Si le serveur Target n’est pas accessible ou si l’utilisateur n’est pas admissible pour la campagne, la valeur defaultContent est renvoyée.

         * **Type :** Targetcallback `<String>`
   * Voici un exemple de code pour cette méthode :

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Pour en savoir plus sur l’API Target sous-jacente, voir [Livraison](https://docs.adobe.com/dev/products/target/reference/delivery.html) dans l’aide des développeurs Target.








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
      Target.setThirdPartyID(“third-party-id”);
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
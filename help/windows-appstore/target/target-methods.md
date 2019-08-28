---
description: Liste des méthodes Target fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-description: Liste des méthodes Target fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-title: Méthodes Target
solution: Marketing Cloud, Analytics
title: Méthodes Target
topic: Développeur et mise en œuvre
uuid: 8 c 35 b 31 c-c 70 b -4 dba -8759-173342 a 301 e 9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Méthodes Target {#target-methods}

Liste des méthodes Target fournies par la bibliothèque Windows 8.1 Universal App Store.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes Analytics est « Target ».

[Les mesures de cycle de vie](/help/windows-appstore/metrics.md) sont envoyées sous la forme de paramètres à chaque chargement de mbox.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Référence de classe : Targetlocationrequest

### Propriétés

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Constantes de chaîne

Ces informations permettent de définir des clés pour les paramètres personnalisés.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **Loadrequest (winjs : Loadrequest)**

   Envoie `request` à votre serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un bloc `callback`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **Createrequest (winjs : Createrequest)**

   Crée un objet `TargetLocationRequest` avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **Createorderconfirmrequest (winjs : Createorderconfirmrequest)**

   Crée un objet `TargetLocationRequest` avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **Clearcookies (winjs : Clearcookies)**

   Efface les cookies Target pour l’application sur l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void ClearCookies(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **Getpcid (winjs : Getpcid)**

   Renvoie le cookie d’ID de PC pour l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **Getsessionid (winjs : Getsessionid)**

   Renvoie le cookie d’ID de session pour l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

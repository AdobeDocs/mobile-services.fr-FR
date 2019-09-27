---
description: Liste des méthodes Target fournies par la bibliothèque Plateforme Windows universelle.
seo-description: Liste des méthodes Target fournies par la bibliothèque Plateforme Windows universelle.
seo-title: Méthodes Target
solution: Marketing Cloud,Analytics
title: Méthodes Target
topic: Développeur et mise en œuvre
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Méthodes Target {#target-methods}

Liste des méthodes Target fournies par la bibliothèque Plateforme Windows universelle.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager.

[Les mesures](/help/universal-windows/metrics.md) de cycle de vie sont envoyées sous forme de paramètres à chaque chargement de mbox.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Référence de classe : TargetLocationRequest

## Propriétés

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Constantes de chaîne

Ces informations vous aident à définir les clés des paramètres personnalisés.

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

* **LoadRequest (winJS : loadRequest)**

   Envoie `request` à votre serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un bloc `callback`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest (winJS : createRequest)**

   Crée un objet `TargetLocationRequest` avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder&#x200B;ConfirmRequest (winJS: createOrder&#x200B;ConfirmRequest)**

   Crée un objet `TargetLocationRequest` avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies (winJS: clearCookies)**

   Efface les cookies Target pour l’application sur l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void ClearCookies();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Renvoie le cookie d’ID de PC pour l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId (winJS: getSessionId)**

   Renvoie le cookie d’ID de session pour l’appareil en cours d’utilisation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```


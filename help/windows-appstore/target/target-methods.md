---
description: Liste des méthodes de Cible fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-description: Liste des méthodes de Cible fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-title: Méthodes Target
solution: Experience Cloud,Analytics
title: Méthodes Target
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 42%

---

# Méthodes Target {#target-methods}

Liste des méthodes de Cible fournies par la bibliothèque Windows 8.1 Universal App Store.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Cible et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Les méthodes Analytics comportent le préfixe &quot;Cible&quot;.

[Les mesures de cycle de vie](/help/windows-appstore/metrics.md) sont envoyées sous la forme de paramètres à chaque chargement de mbox.

>[!TIP]
>
>Lorsque vous utilisez des méthodes `winmd` de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre avec un caractère minuscule.

## Référence de classe : TargetLocationRequest

### Propriétés

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

* **LoadRequest (winJS: loadRequest)**

   Envoie `request` à votre serveur de Cibles configuré et renvoie la valeur de chaîne de l&#39;offre générée dans un bloc `callback`.

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

* **CreateRequest (winJS: createRequest)**

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

* **CreateOrder &#x200B; ConfirmRequest (winJS : createOrder &#x200B; ConfirmRequest)**

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

* **ClearCookies (winJS: clearCookies)**

   Efface les cookies de Cible de l’application sur le périphérique actuel.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void ClearCookies(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS : getPcId)**

   Renvoie le cookie d&#39;ID de PC pour le périphérique actuel.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS : getSessionId)**

   Renvoie le cookie ID de session pour le périphérique actuel.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

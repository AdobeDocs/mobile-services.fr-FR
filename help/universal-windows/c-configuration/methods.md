---
description: Classes et méthodes fournies par la bibliothèque Plateforme Windows universelle.
seo-description: Classes et méthodes fournies par la bibliothèque Plateforme Windows universelle.
seo-title: Méthodes SDK
solution: Marketing Cloud, Analytics
title: Méthodes SDK
topic: Développeur et mise en œuvre
uuid: e 3 aa 41 d 6-7 bc 0-4208-a 662-12907 c 209 a 77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Classes et méthodes fournies par la bibliothèque Plateforme Windows universelle.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs : Getversion)**

   Renvoie la version actuelle de la bibliothèque Adobe Mobile.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **Getprivacystatusasync (winjs : Getprivacystatusasync)**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

   * `ADBMobilePrivacyStatusOptIn` - Les accès sont envoyés immédiatement.
   * `ADBMobilePrivacyStatusOptOut` - Les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      The default value is set in the `ADBMobileConfig.json` config file. Pour plus d'informations, voir [Fichier de configuration adbmobileconfig. json](/help/universal-windows/c-configuration/c.json.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Voici les exemples de code pour cette méthode :

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript **

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **Setprivacystatus (winjs : Setprivacystatus)**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`. Valeurs possibles :
   * `ADBMobilePrivacyStatusOptIn` - les accès sont envoyés immédiatement.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `DBMobilePrivacyStatusUnknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés. Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      * Voici la syntaxe de cette méthode :

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Voici les exemples de code pour cette méthode :

         **C-sharp**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript **

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **Getlifetimevalue (winjs : Getlifetimevalue)**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est `0`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **Getuseridentifier (winjs : Getuseridentifier)**

   Renvoie un identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini. Returns `null` if a custom identifier is not set.
La valeur par défaut est `null`.

   >[!IMPORTANT]
   >
   >Si votre application est mise à niveau depuis le SDK Experience Cloud 3. x vers 4. x, le service d'ID précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu'identificateur d'utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `null` tant qu’il n’a pas été défini.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs : Setuseridentifier)**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **Getdebuglogging (winjs : Getdebuglogging)**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static bool GetDebugLogging();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **Setdebuglogging (winjs : Setdebuglogging)**

   Définit la préférence de journalisation de débogage sur `debugLogging`. La journalisation du débogage ne fonctionne que lorsque vous utilisez la version de débogage de la bibliothèque, la version de publication ignore ce paramètre.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **Collectlifecycledata (winjs : Collectlifecycledata)**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. For more information, see  [Lifecycle metrics](/help/universal-windows/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **Pausecollectinglifecycledata (winjs : Pausecollectinglifecycledata)**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, en cas de suspension, collecte un horodatage afin de déterminer la durée de la session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/universal-windows/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```

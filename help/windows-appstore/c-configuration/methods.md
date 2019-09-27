---
description: Classes et méthodes fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.
seo-description: Classes et méthodes fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.
seo-title: Méthodes SDK
solution: Marketing Cloud,Analytics
title: SDK methods
topic: Développeur et mise en œuvre
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Classes et méthodes fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion (winJS : getVersion)**

   Renvoie la version actuelle de la bibliothèque Adobe Mobile.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS : getPrivacyStatusAsync)**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Here are the code samples for this method:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus (winJS : setPrivacyStatus)**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`. Valeurs possibles :

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue (winJS : getLifetimeValue)**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est de 0.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static float GetLifetimeValue();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier (winJS : getUserIdentifier)**

   Renvoie un identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie une valeur nulle si aucun identifiant personnalisé n’est défini. La valeur par défaut est `null`.

   >[!TIP]
   >
   >Si votre application effectue une mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’ID précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `null` tant qu’il n’est pas défini.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS : setUserIdentifier)**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging (winJS : getDebugLogging)**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging (winJS : setDebugLogging)**

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

* **CollectLifecycleData (winJS : VEraieLifecycleData)**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. Il est également recommandé de transmettre l’activité ou le service comme objet de contexte au lieu du contexte d’application globale.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollecting&#x200B;LifecycleData (winJS: pauseCollecting&#x200B;LifecycleData)**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, en cas de suspension, collecte un horodatage afin de déterminer la durée de la session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. Il est également recommandé de transmettre l’activité ou le service comme objet de contexte au lieu du contexte d’application globale.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```

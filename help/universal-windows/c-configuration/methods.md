---
description: Classes et méthodes fournies par la bibliothèque Plateforme Windows universelle.
solution: Experience Cloud,Analytics
title: Méthodes SDK
topic-fix: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
exl-id: 0aac477c-074d-457c-b117-bb205119c475
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 67%

---

# Méthodes SDK {#sdk-methods}

Classes et méthodes fournies par la bibliothèque Plateforme Windows universelle.

>[!TIP]
>
>Lorsque vous utilisez des méthodes `winmd` de winJS (JavaScript), la première lettre de toutes les méthodes est automatiquement mise en minuscule.

* **GetVersion (winJS: getVersion)**

   Renvoie la version actuelle de la bibliothèque Adobe Mobile.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS) : getPrivacyStatusAsync)**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

   * `ADBMobilePrivacyStatusOptIn` - Les accès sont envoyés immédiatement.
   * `ADBMobilePrivacyStatusOptOut` - Les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      La valeur par défaut est définie dans le fichier de configuration `ADBMobileConfig.json`. Pour plus d’informations, voir [Fichier de configuration ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Voici des exemples de code pour cette méthode :

      **Accentuation C**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS) : setPrivacyStatus)**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`. Valeurs possibles :
   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `DBMobilePrivacyStatusUnknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés. Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      * Voici la syntaxe de cette méthode :

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Voici des exemples de code pour cette méthode :

         **Accentuation**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS : getLifetimeValue)**

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

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Renvoie l’identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie `null` si aucun identifiant personnalisé n’est défini.
La valeur par défaut est `null`.

   >[!IMPORTANT]
   >
   >Si votre application est mise à niveau du SDK Experience Cloud 3.x vers 4.x, le service d’ID précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant d’utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `null` tant qu’il n’a pas été défini.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

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

* **GetDebugLogging (winJS: getDebugLogging)**

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

* **SetDebugLogging (winJS: setDebugLogging)**

   Définit la préférence de journalisation de débogage sur `debugLogging`. La journalisation de débogage fonctionne uniquement lors de l’utilisation de la version de débogage de la bibliothèque. La version de publication ignore ce paramètre.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/universal-windows/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS : pauseCollecting &#x200B; LifecycleData)**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, lors de la mise en pause, collecte un horodatage pour déterminer la durée de la session précédente. Cela définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/universal-windows/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```

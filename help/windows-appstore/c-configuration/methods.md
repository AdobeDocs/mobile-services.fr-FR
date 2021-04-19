---
description: Classes et méthodes fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-description: Classes et méthodes fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-title: Méthodes SDK
solution: Experience Cloud,Analytics
title: Méthodes SDK
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 50%

---

# Méthodes SDK {#sdk-methods}

Classes et méthodes fournies par la bibliothèque Windows 8.1 Universal App Store.

>[!TIP]
>
>Lorsque vous utilisez des méthodes `winmd` de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre avec un caractère minuscule.

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

   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - Si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      La valeur par défaut est définie dans le fichier [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Voici des exemples de code pour cette méthode :

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

   * `ADBMobilePrivacyStatusOptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` - Si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

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

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est de 0.

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

   Renvoie l’identifiant utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie la valeur null si aucun identifiant personnalisé n’est défini. La valeur par défaut est `null`.

   >[!TIP]
   >
   >Si votre application est mise à niveau de l’Experience Cloud SDK 3.x vers 4.x, l’ID précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Cela permet de conserver les données du visiteur entre les mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant utilisateur est `null` jusqu’à ce qu’il soit défini.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
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

   Définit la préférence de journalisation de débogage sur `debugLogging`. La journalisation du débogage fonctionne uniquement lors de l’utilisation de la version de débogage de la bibliothèque. La version de publication ignore ce paramètre.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData (winJS : VE)**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Appelez cette méthode dans la méthode `onResume()` de chaque Activité de votre application, comme indiqué dans l&#39;exemple suivant. Nous vous recommandons également de transmettre l’Activité ou le service en tant qu’objet de contexte plutôt que le contexte d’application globale.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollecte &#x200B; LifecycleData (winJS : pauseCollecte &#x200B; données de cycle de vie)**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, lors d’une mise en pause, un horodatage est collecté pour déterminer la durée de session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Appelez cette méthode dans les méthodes `onPause()` de chaque Activité de votre application, comme indiqué dans l&#39;exemple. Nous vous recommandons également de transmettre l’Activité ou le service en tant qu’objet de contexte plutôt que le contexte d’application globale.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```

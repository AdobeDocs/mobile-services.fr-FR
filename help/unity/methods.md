---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Méthodes ADBMobile.cs
solution: Experience Cloud
title: Méthodes ADBMobile.cs
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 70%

---


# Méthodes ADBMobile.cs {#adbmobile-cs-methods}

## Méthodes de configuration

* **CollectLifecycleData**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications (iOS uniquement)**

   Activez les notifications locales dans votre application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void EnableLocalNotifications();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static bool GetDebugLogging();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel.

   * Voici la syntaxe de cette méthode :

      ```java
      public static double GetLifetimeValue();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.
   * `MOBILE_PRIVACY_STATUS_OPT_IN` : les accès sont immédiatement envoyés.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT` : les accès sont ignorés.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).

      Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).
The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) file.

   * Voici la syntaxe de cette méthode :

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Renvoie l’identifiant utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie la valeur null si aucun identifiant personnalisé n’est défini. La valeur par défaut est `null`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string GetUserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   Obtient la version de la bibliothèque.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string GetVersion();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (iOS uniquement)**

   Indique au SDK que la prochaine reprise depuis l’arrière-plan ne doit pas commencer une nouvelle session, quelle que soit la valeur de temporisation de la session du cycle de vie dans le fichier de configuration.

   >[!TIP]
   >
   >Cette méthode est destinée à être utilisée pour les applications qui s’inscrivent aux notifications en arrière-plan et doit uniquement être appelée à partir du code qui s’exécute pendant que votre application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (Android uniquement)**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, lors d’une mise en pause, un horodatage est collecté pour déterminer la durée de session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (Android uniquement)**

   Indique au SDK qu’il doit définir son contexte d’application à partir de l’activité actuelle d’UnityPlayer.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetContext();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Définit la préférence de journalisation du débogage sur Activé.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Définit l’état de confidentialité de l’utilisateur actuel. Valeurs possibles :

   * `MOBILE_PRIVACY_STATUS_OPT_IN` : les accès sont immédiatement envoyés.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT` : les accès sont ignorés.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Voici un exemple de code pour cette syntaxe :

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Définit l’identifiant utilisateur sur userId.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Méthodes Analytics

* **GetTrackingIdentifier**

   Récupère l’identifiant de suivi des analyses.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. Les états sont les vues disponibles dans votre application, telles que &quot;écran de titre&quot;, &quot;niveau 1&quot;, &quot;pause&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `TrackState` incrémentent les pages vues.

   Si l’état est vide, il s’affiche comme *`app name app version (build)`* dans les rapports. If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Effectue le suivi d’une action dans votre application. Les actions sont les éléments qui se produisent dans votre application que vous souhaitez mesurer, tels que &quot;décès&quot;, &quot;niveau de gain&quot;, &quot;abonnements de flux&quot; et d’autres mesures.

   >[!TIP]
   >
   >Si vous avez du code qui peut s’exécuter pendant que l’application est en arrière-plan (par exemple, une récupération de données en arrière-plan), utilisez plutôt `trackActionFromBackground`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (iOS uniquement)**

   Effectue le suivi d’une action survenue en arrière-plan. Cela empêche les événements de cycle de vie de se déclencher dans certains scénarios.

   >[!TIP]
   >
   >Invoquez cette méthode uniquement dans le code qui s’exécute pendant que l’application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envoie les coordonnées de latitude et de longitude actuelles. Utilise également les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point d’intérêt défini, une variable de données contextuelles est renseignée et envoyée avec l’appel TrackLocation.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   Effectue un suivi quand un utilisateur entre à proximité d’une balise.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   Efface les données de balise une fois qu’un utilisateur n’est plus à proximité de la balise.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueAugmentation**

   Les Ajoutes correspondent à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   Commence une action minutée par l’action du nom. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Transmettez les données pour mettre à jour les données contextuelles associées à l’action donnée. Les données transmises sont ajoutées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’action.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Termine une action minutée.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   Renvoie si une action minutée est ou non en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   Force la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne, peu importe le nombre d’accès déjà dans la file d’attente.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackingClearQueue();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Récupère le nombre d’accès actuellement dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Méthodes d’identification des Experience Cloud

* **GetMarketingCloudID**

   Récupère l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string GetMarketingCloudID();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Avec l’ID d’Experience Cloud, vous pouvez définir d’autres ID de client à associer à chaque visiteur. L’API du Visiteur accepte plusieurs ID de client pour le même visiteur, ainsi qu’un identifiant de type de client afin de séparer la portée des différents ID de client. Cette méthode correspond aux setCustomerIDs dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## Méthodes d’acquisition

* **ProcessGooglePlayInstallReferrerUrl** *(Android uniquement)*

   Transférez l’URL de parrain renvoyée par un appel à l’API du Parrain d’installation de Google Play à cette méthode.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```

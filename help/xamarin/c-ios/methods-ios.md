---
description: Méthodes iOS pour les composants Xamarin pour le SDK 4.x des solutions Experience Cloud.
keywords: Xamarin
seo-description: Méthodes iOS pour les composants Xamarin pour le SDK 4.x des solutions Experience Cloud.
seo-title: iOS methods
solution: Marketing Cloud,Développeur
title: Méthodes iOS
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: f53953831e6471ea64eb2ae06ddae16ca0eab6f6

---


# iOS methods{#ios-methods}

Méthodes iOS pour les composants Xamarin pour le SDK 4.x des solutions Experience Cloud.

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Définit la préférence de consignation de débogage à activer.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static double LifetimeValue();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.
   * `ADBMobilePrivacyStatus.OptIn` - les accès sont envoyés immédiatement.
   * `ADBMobilePrivacyStatus.OptOut` - les accès sont ignorés.
   * ADBMobilePrivacyStatus.Unknown : si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Si le suivi hors ligne est désactivé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.
   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   Définit l’état de confidentialité pour l’utilisateur actuel. Valeurs possibles :
   * `ADBMobilePrivacyStatus.OptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatus.OptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatus.Unknown` : si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Renvoie un identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie une valeur nulle si aucun identifiant personnalisé n’est défini. La valeur par défaut est `null`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Renvoie un identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini. Renvoie une valeur nulle si aucun identifiant personnalisé n’est défini. La valeur par défaut est `null`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string UserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Obtient la version de la bibliothèque.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string Version();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (iOS seulement)**

   Indique au SDK que la prochaine reprise depuis l’arrière-plan ne doit pas commencer une nouvelle session, quelle que soit la valeur de temporisation de la session du cycle de vie dans le fichier de configuration.

   >[!TIP]
   >
   >Cette méthode est conçue pour être utilisée pour les applications qui s’inscrivent aux notifications en arrière-plan et qui doivent uniquement être appelées à partir du code qui s’exécute pendant que votre application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Récupère l’identifiant de suivi des analyses.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. Les états sont les vues disponibles dans l’application, par exemple « écran de titre », « niveau 1 », « pause », etc. Ces états sont similaires aux pages d’un site Web et `TrackState` les appels incrémentent les pages vues. Si l’état est vide, il s’affiche sous la forme "nom de l’application version de l’application (compilation)" dans les rapports. Si vous voyez cette valeur dans les rapports, veillez à définir state dans chaque appel `TrackState`.

   [!TIP]
   >This is the only tracking call that increments page views.
   >
   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Effectue le suivi d’une action dans l’application. Les actions sont les événements qui se produisent dans l’application et que vous souhaitez mesurer, par exemple « décès », « niveau atteint », « abonnements aux flux » et autres mesures.

   >[!TIP]
   If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (iOS seulement)**

   Effectue le suivi d’une action survenue en arrière-plan. Ceci empêche les événements de cycle de vie de se déclencher dans certains scénarios.

   >[!TIP]
   Cette méthode ne doit être appelée que dans le code qui s’exécute pendant que votre application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envoie les coordonnées de latitude et de longitude actuelles. Utilise également les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `TrackLocation`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Effectue un suivi quand un utilisateur entre à proximité d’une balise.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Efface les données de balise une fois qu’un utilisateur n’est plus à proximité de la balise.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Ajoute une quantité à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      public nbsp;static void TrackLifetimeValueAugmentation(double quantité, données NSDictionary);

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Commence une action minutée par l’action du nom. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Transmet des données afin de mettre à jour les données contextuelles associées à l’action donnée. Les données transmises sont annexées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’action.

   >[!TIP]
   Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Termine une action minutée.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   Renvoie si une action minutée est (ou non) en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Force la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne, peu importe le nombre d’accès déjà dans la file d’attente.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Récupère le nombre d’accès actuellement dans la file d’attente hors ligne.

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Récupère l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Avec l’identifiant Experience Cloud, vous pouvez définir d’autres identifiants de client à associer à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour le même visiteur, ainsi qu’un identifiant de type Client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants setCustomerID dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Méthodes Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   Constructeur de commodité permettant de créer un objet `ADBTargetLocationRequest` avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Crée une `ADBTargetLocationRequest`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Efface les cookies de ciblage de l’application.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Renvoie le dernier profil du visiteur obtenu. Renvoie nul si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `NSUserDefaults` pour un accès facile à l’échelle de plusieurs lancements de l’application.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Renvoie le DPID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Renvoie le DPUUID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Définit le dpid et le dpuuid. Si dpid et dpuuid sont définis, ils seront envoyés avec chaque signal.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Réinitialise l’UUID du gestionnaire d’audience et purge le profil du visiteur en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void AudienceReset ();
      ```

   * Voici la syntaxe de cette méthode :

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Vidéo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Pour en savoir plus, voir la section [Analyses de vidéos](/help/ios/getting-started/dev-qs.md).

* **MediaCreateSettings**

   Renvoie un objet `ADBMediaSettings` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Renvoie un objet `ADBMediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Ouvre un objet `ADBMediaSettings` pour le suivi.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Ferme le nom nommé de l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Lit le nom nommé de l’élément multimédia au décalage donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Marque manuellement l’élément multimédia comme terminé au décalage donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage donné.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```

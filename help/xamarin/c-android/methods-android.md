---
description: Méthodes Android pour les composants Xamarin pour le SDK des solutions Experience Cloud 4.x.
keywords: Xamarin
seo-description: Méthodes Android pour les composants Xamarin pour le SDK des solutions Experience Cloud 4.x.
seo-title: Méthodes Android
solution: Marketing Cloud,Developer
title: Méthodes Android
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 66%

---


# Méthodes Android{#android-methods}

Méthodes Android pour les composants Xamarin pour le SDK des solutions Experience Cloud 4.x.

## Méthodes de configuration {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Renvoie la préférence de consignation de débogage actuelle et la valeur par défaut est false.

   * Voici la syntaxe de cette méthode :

      ```java
      public static Boolean DebugLogging;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **Valeur de durée de vie**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel.

   * Voici la syntaxe de cette méthode :

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.
   * `ADBMobilePrivacyStatus.OptIn` - les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatus.OptOut` - les accès sont ignorés.
   * `ADBMobilePrivacyStatus.Unknown` - si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés). Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

   The default value is set in the [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) file.

   * Voici la syntaxe de cette méthode :

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Si un identifiant personnalisé a été défini, renvoie cet identifiant. Si aucun identifiant personnalisé n’est défini, renvoie null. La valeur par défaut est `null`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static UserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Version**

   Obtient la version de la bibliothèque.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string Version;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, lors d’une mise en pause, un horodatage est collecté pour déterminer la durée de session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache correctement que l’application n’a pas planté. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (activité Activité)**

   (4.2 ou version ultérieure) Indique au SDK que les données de cycle de vie doivent être collectées pour être utilisées dans toutes les solutions du SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (activité Activité)**

   (4.2 ou version ultérieure) Indique au SDK que les données de cycle de vie doivent être collectées pour être utilisées dans toutes les solutions du SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 ou version ultérieure) Permet de charger un autre fichier `ADBMobile JSON` de configuration lorsque l’application début. Cette autre configuration est utilisée jusqu’à la fermeture de l’application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 ou version ultérieure) Définit la grande icône utilisée pour les notifications créées par le SDK. Cette icône est l’image principale affichée lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notifications.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 ou version ultérieure) Définit la petite icône utilisée pour les notifications créées par le SDK. Cette icône s’affiche dans la barre d’état et représente l’image secondaire affichée lorsque l’utilisateur voit la notification complète dans le centre de notification.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Méthodes Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Renvoie l’identifiant généré automatiquement pour Analytics. Il s’agit d’un identifiant unique propre à l’application qui est généré au lancement initial et qui est stocké et utilisé à partir de ce moment. Cet identifiant est conservé entre les mises à niveau de l’application et supprimé lors de la désinstallation.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string TrackingIdentifier;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. `States` sont les vues disponibles dans votre application, telles que &quot;écran de titre&quot;, &quot;niveau 1&quot;, &quot;pause&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `TrackState` incrémentent les pages vues. Si l’état est vide, il s’affiche sous la forme &quot;nom de l’application version de l’application (compilation)&quot; dans les rapports. If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Effectue le suivi d’une action dans votre application. Les actions sont les éléments qui se produisent dans votre application que vous souhaitez mesurer, tels que &quot;décès&quot;, &quot;niveau de gain&quot;, &quot;abonnements de flux&quot; et d’autres mesures.

   >[!TIP]
   >
   >
   >Si vous avez du code qui peut s’exécuter pendant que l’application est en arrière-plan (par exemple, une récupération de données en arrière-plan), utilisez plutôt `trackActionFromBackground`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Envoie les coordonnées de latitude et de longitude actuelles. Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `TrackLocation`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Effectue un suivi quand un utilisateur entre à proximité d’une balise.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Efface les données de balise une fois qu’un utilisateur n’est plus à proximité de la balise.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueAugmentation**

   Ajoute une quantité à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Commence une action minutée par l’action du nom. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   > Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Voici un exemple de code pour cette méthode :

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Transmettez les données pour mettre à jour les données contextuelles associées à l’action donnée. Les données transmises sont ajoutées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’action.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Termine une action minutée.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Renvoie si une action minutée est ou non en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Force la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne, quel que soit le nombre d’accès actuellement en file d’attente.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SendQueuedHits();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void ClearQueue(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Récupère le nombre d’accès actuellement dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      public static long QueueSize(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Méthodes d’identification des Experience Cloud {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Récupère l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string MarketingCloudId;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Avec l’ID d’Experience Cloud, vous pouvez définir d’autres ID de client à associer à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour un même visiteur, ainsi qu’un identifiant de type client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants `setCustomerIDs` dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Méthodes Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Crée une `ADBTargetLocationRequest`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Efface les cookies de Cible de votre application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void ClearCookies(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **Profil du visiteur**

   Renvoie le dernier profil du visiteur obtenu. Renvoie nil si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `NSUserDefaults` pour un accès facile à l’échelle de plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string Dpuuid; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static string AudienceDpuuid; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Définit la valeur `dpid` et `dpuuid`. Si `dpid` et `dpuuid` sont définis, ils sont envoyés avec chaque signal.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Réinitialiser le**

   Resets audience manager `UUID` and purges current visitor profile.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Reset ();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       AudienceManager.Reset ();
      ```

## Vidéo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Pour plus d’informations sur les analyses vidéo, voir Analyses [](/help/android/analytics-main/video-qs.md)vidéo.

* **MediaSettings**

   Renvoie un objet `MediaSettings` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Renvoie un objet `MediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.

   * Voici la syntaxe de cette méthode :

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Ouvrir**

   Ouvre un objet `ADBMediaSettings` pour le suivi.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Fermer**

   Ferme l’élément multimédia nommé name.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Close(string name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Close (settings.Name); 
      ```

* **Play**

   Lit le nom nommé de l’élément multimédia au décalage donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Terminée**

   Marque manuellement l’élément multimédia comme terminé au décalage offset donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stopper**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage offset donné.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Cliquez sur**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Piste**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.Track (settings.Name, null); 
      ```

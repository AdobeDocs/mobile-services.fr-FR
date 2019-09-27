---
description: Liste des méthodes fournies par la bibliothèque Android.
keywords: android;library;mobile;sdk
seo-description: Liste des méthodes fournies par la bibliothèque Android.
seo-title: Méthodes de configuration
solution: Marketing Cloud,Analytics
title: Méthodes de configuration
topic: Développeur et mise en œuvre
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Configuration methods{#configuration-methods}

Liste des méthodes fournies par la bibliothèque Android.

## Initial configuration {#section_9169243ECC4744A899A8271F92090ECD}

La méthode suivante doit être appelée une fois dans la méthode `onCreate` de l’activité principale :

* `setContext`Voici l’exemple de code pour cette méthode :

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ````


## SDK settings (Config Class) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Enregistre un objet qui implémente l’interface `AdobeDataCallback`. The overwritten "call" method will be invoked with a `Config.MobileDataEvent` value and the associated data in a `Map<String, Object>` for the triggering event. Pour plus d’informations sur les événements qui déclencheront ce rappel, voir *MobileDataEventEnum* au bas de cette rubrique.

      >[!TIP]
      >
      >Cette méthode nécessite la version 4.9.0 ou ultérieure.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Renvoie la version actuelle de la bibliothèque Adobe Mobile.
   * Voici la syntaxe de cette méthode :

      ```java
      public static String getVersion();
      ```

   * Here is a code example for this method:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Renvoie la représentation d’énumération de l’état de confidentialité pour l’utilisateur actuel.

      Vous trouverez ci-dessous les valeurs de l’état de confidentialité :

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, où les accès sont envoyés immédiatement.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, où les siens sont ignorés.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` : si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés).

         Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ». La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.
   * Voici la syntaxe de cette méthode :

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Here is a code sample for this method:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Définit l’état de confidentialité pour l’utilisateur actuel sur `status`.

      Vous pouvez définir l’état de confidentialité sur l’une des valeurs suivantes :
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, où les accès sont envoyés immédiatement. Ces accès sont envoyés immédiatement.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, où les siens sont ignorés. Ces accès sont ignorés.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` : si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés).
Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Here is a code sample for this method:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est `0`.

   * Voici la syntaxe de cette méthode :

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Here is a code sample for this method:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Si un identifiant personnalisé a été défini, l’identifiant de l’utilisateur personnalisé est renvoyé. Si aucun identifiant personnalisé n’a été défini, la valeur `null` est renvoyée. La valeur par défaut est `null`.

      >[!TIP]
      >
      >Si votre application effectue une mise à niveau d’Experience Cloud 3.x vers le SDK 4.x, l’identifiant visiteur personnalisé ou généré automatiquement précédent est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Ceci permet de conserver les données visiteur entre les différentes mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur est `null` jusqu’à ce qu’il soit défini.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Définit l’identifiant d’utilisateur sur `identifier`.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Renvoie la préférence de consignation de débogage actuelle. La valeur par défaut est `false`.
   * Voici la syntaxe de cette méthode :

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Définit la préférence de journalisation de débogage sur `debugLogging`.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/configuration/methods.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Avec données contextuelles supplémentaires :

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**Version 4.2 ou supérieure**) Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).
   * Voici la syntaxe de cette méthode :

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * Indique au SDK que l’application est suspendue, de sorte que les mesures de cycle de vie sont correctement calculées. Par exemple, `onPause` collecte un horodatage afin de déterminer la durée de la session précédente. Ceci définit également un indicateur de sorte que le cycle de vie sache que l’application n’a pas planté. Pour plus d’informations, voir [Mesures de cycle de vie](/help/android/metrics.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Version 4.2 ou supérieure**) Définit la petite icône qui sera utilisée pour les notifications créées par le SDK. Cette icône apparaît dans la barre d’état et sera l’image secondaire qui s’affiche lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notifications.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Version 4.2 ou supérieure**) Définit la grande icône qui sera utilisée pour les notifications créées par le SDK. Cette icône sera l’image principale affichée lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notifications.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Version 4.2 ou supérieure**) Permet de charger un fichier de configuration JSON ADBMobile distinct au démarrage de l’application. Cette autre configuration est utilisée jusqu’à la fermeture de l’application.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Définit le jeton d’appareil pour les notifications Push.
   * Voici la syntaxe de cette méthode :

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Fournit un joignable au SDK qui renvoie la chaîne de l’identifiant de publicité renvoyé par les services Google Play. Le SDK exécute cette tâche sur un fil en arrière-plan et définit une variable interne pour l’identifiant de publicité qui est basée sur la valeur renvoyée depuis le joignable.

      >[!IMPORTANT]
      > 
      >If you want to use the Advertising Identifier in Acquisition or Lifecycle, call it before calling `Config.collectLifecycleData`.

      * Voici la syntaxe de cette méthode :

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Voici l’exemple de code pour cette méthode :

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## Interface AdobeDataCallback {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```

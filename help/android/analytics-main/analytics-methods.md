---
description: Liste des méthodes Adobe Analytics fournies par la bibliothèque Android.
keywords: android ; library ; mobile ; sdk
seo-description: Liste des méthodes Adobe Analytics fournies par la bibliothèque Android.
seo-title: Méthodes Analytics
solution: Marketing Cloud, Analytics
title: Méthodes Analytics
topic: Développeur et mise en œuvre
uuid: ac 7 c 640 e -9 dcc -4724-b 561-019 cc 025 d 5 a 7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Liste des méthodes Adobe Analytics fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud], y compris Analytics], Target], Audience Manager] et le service d'identité Adobe Experience Platform]. Un préfixe est attribué aux méthodes selon la solution. Par exemple, les méthodes d’Experience Cloud ID sont affectées du préfixe `analytics`.

Chacune des méthodes suivantes est utilisée pour envoyer des données vers la suite de rapports Adobe Analytics :

* **trackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

   If `state` is empty, `app name app version (build)` is displayed in reports. Si cette valeur s’affiche dans les rapports, assurez-vous que vous avez défini `state` dans chaque appel `trackState`.

   >[!TIP]
   >
   >Il s'agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **Trackaction**
suit une action dans votre application.

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * Voici la syntaxe de cette méthode :

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **Gettrackingidentifier**
Renvoie l'identifiant visiteur généré automatiquement pour Analytics.

   Il s’agit d’un identifiant visiteur unique spécifique à l’application, généré au lancement initial, puis stocké et utilisé à partir de ce lancement. L’identifiant est conservé d’une mise à niveau à l’autre, puis supprimé lorsque l’application est désinstallée.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   Envoie la latitude, la longitude et l'emplacement actuels d'un point ciblé défini. Pour plus d'informations, voir [Géolocalisation et points ciblés](/help/android/location/geo-poi.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Commence une minutée portant le nom `action`action.

   Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Transmet `contextData` pour mettre à jour les données contextuelles associées à l’`action`. Les données `data` transmises sont ajoutées aux données existantes pour l’action et, si la même clé est déjà définie pour `action`, écrase les données.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * Voici un exemple de code pour cette méthode :

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Termine une action minutée. Si vous fournissez `block`, vous pouvez accéder aux valeurs temporelles finales et manipuler `data` avant d’envoyer l’accès final.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **Nécessite SDK 4.1.**

   Quel que soit le nombre d’accès mis en file d’attente, cette méthode force la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      voidsendQueuedHits()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Renvoie le nombre d’appels de suivi stockés dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      long getQueueSize()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```java
      voidclearQueue()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Soyez prudent lorsque vous effacez manuellement la file d’attente. Cette action est irréversible.
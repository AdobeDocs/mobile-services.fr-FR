---
description: Informations pour vous aider à utiliser le SDK Plateforme Windows universelle avec Adobe Analytics.
seo-description: Informations pour vous aider à utiliser le SDK Plateforme Windows universelle avec Adobe Analytics.
seo-title: Méthodes Analytics
solution: Marketing Cloud, Analytics
title: Méthodes Analytics
topic: Développeur et mise en œuvre
uuid: cc 299 bb 5-ec 61-49 bf -869 a-f 3 c 3 bc 83359 f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Informations pour vous aider à utiliser le SDK Plateforme Windows universelle avec Adobe Analytics.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes Analytics est « Analytics ».

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs : Trackstate)**

   Effectue le suivi de l’état d’une application avec les données contextuelles facultatives. Les états correspondent aux affichages disponibles dans l’application : tableau de bord d’accueil, paramètres d’application, panier, etc. Ces états sont semblables aux pages d’un site web ; les appels `TrackState` incrémentent les pages vues.
Si `state` est vide, il est présenté comme « app name app version (build) » dans les rapports. Si vous voyez cette valeur dans les rapports, veillez à définir `state` dans chaque appel `TrackState`.

   >[!TIP]
   >
   >Il s'agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs : Trackaction)**

   Effectue le suivi d’une action dans l’application. Les actions sont les événements qui se produisent dans l’application et que vous souhaitez mesurer, par exemple les connexions, les appuis sur la bannière, les abonnements aux flux, etc.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **Gettrackingidentifierasync (winjs : Gettrackingidentifierasync)**

   Renvoie l’identifiant visiteur automatiquement généré pour Analytics. Il s’agit d’un identifiant visiteur unique et spécifique à l’application généré au lancement initial, puis stocké et utilisé à partir de ce lancement. Cet identifiant est conservé d’une mise à niveau de l’application à l’autre, puis supprimé à la désinstallation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **Tracklocation (winjs : Tracklocation)**

   Envoie les coordonnées x et y actuelles. Utilise également les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **Tracklifetimevalueincrease (winjs : Tracklifetimevalueincrease)**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **Tracktimedactionstart (winjs : Tracktimedactionstart)**

   Commence une minutée portant le nom `action`action. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **Tracktimedactionupdate (winjs : Tracktimedactionupdate)**

   Transmet `contextData` afin de mettre à jour les données contextuelles associées à l’`action` donnée. Les `data` (données) transmises sont ajoutées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’`action`.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **Tracktimedactionexissasync (winjs : Tracktimedactionexissasync)**

   Renvoie true si l'action minutée donnée existe et false s'il n'existe pas.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs : Tracktimedactionend)**

   Termine une action minutée.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs : Cleartrackingqueue)**

   Efface tous les accès stockés de la file d’attente de suivi Analytics.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs : Getqueuesizeasync)**

   Renvoie le nombre d’accès actuellement stockés dans la file d’attente Analytics.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```

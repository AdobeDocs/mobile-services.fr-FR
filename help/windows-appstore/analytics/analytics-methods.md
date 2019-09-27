---
description: Informations relatives à l’utilisation du SDK Boutique d’applications Windows 8.1 universelle avec Adobe Analytics.
seo-description: Informations relatives à l’utilisation du SDK Boutique d’applications Windows 8.1 universelle avec Adobe Analytics.
seo-title: Méthodes Analytics
solution: Marketing Cloud,Analytics
title: Méthodes Analytics
topic: Développeur et mise en œuvre
uuid: 79db105c-216c-4061-97f3-a55954995e67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Informations relatives à l’utilisation du SDK Boutique d’applications Windows 8.1 universelle avec Adobe Analytics.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud], y compris Analytics], Target] et Audience Manager]. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes Analytics est « Analytics ».

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **TrackState (winJS : trackState)**

   Effectue le suivi de l’état d’une application avec les données contextuelles facultatives. Les états correspondent aux affichages disponibles dans l’application : tableau de bord d’accueil, paramètres d’application, panier, etc. Ces états sont semblables aux pages d’un site web ; les appels `TrackState` incrémentent les pages vues. Si `state` est vide, il est présenté comme « app name app version (build) » dans les rapports. Si vous voyez cette valeur dans les rapports, veillez à définir `state` dans chaque appel `TrackState`.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS : trackAction)**

   Effectue le suivi d’une action dans l’application. Les actions sont les événements qui se produisent dans l’application et que vous souhaitez mesurer, par exemple les connexions, les appuis sur la bannière, les abonnements aux flux, etc.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **GetTrackingIdentifierAsync (winJS : getTrackingIdentifierAsync)**

   Renvoie l’identifiant visiteur automatiquement généré pour Analytics. Il s’agit d’un identifiant visiteur unique spécifique à l’application généré au lancement initial puis stocké et utilisé à partir de ce lancement. Cet identifiant est conservé d’une mise à niveau de l’application à l’autre, puis supprimé à la désinstallation.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **TrackLocation (winJS : trackLocation)**

   Envoie les coordonnées x et y actuelles. Utilise également les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **TrackLifetime &#x200B; ValueAugmentation (winJS : trackLifetime &#x200B; ValueAugmentation)**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **TrackTimed &#x200B; ActionStart (winJS : trackTimed &#x200B; ActionStart)**

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
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS : trackTimed &#x200B; ActionUpdate)**

   Transmet `contextData` afin de mettre à jour les données contextuelles associées à l’`action` donnée. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **TrackTimedActionExistsAsync (winJS : trackTimedActionExistsAsync)**

   Renvoie true si l’action minutée donnée existe et false si ce n’est pas le cas.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS : trackTimed &#x200B; ActionEnd)**

   Termine une action minutée.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS : clearTrackingQueue)**

   Efface tous les accès stockés de la file d’attente de suivi Analytics.

   * Here is the syntax for this message:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Voici l’exemple de code :

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS : getQueueSizeAsync)**

   Renvoie le nombre d’accès actuellement stockés dans la file d’attente Analytics.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```

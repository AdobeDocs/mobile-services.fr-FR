---
description: Informations relatives à l’utilisation du SDK Windows 8.1 Universal App Store avec Adobe Analytics.
seo-description: Informations relatives à l’utilisation du SDK Windows 8.1 Universal App Store avec Adobe Analytics.
seo-title: Méthodes Analytics
solution: Experience Cloud,Analytics
title: Méthodes Analytics
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 52%

---

# Méthodes Analytics {#analytics-methods}

Informations relatives à l’utilisation du SDK Windows 8.1 Universal App Store avec Adobe Analytics.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Cible et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Les méthodes Analytics comportent le préfixe &quot;Analytics&quot;.

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

>[!TIP]
>
>Lorsque vous utilisez des méthodes `winmd` de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre avec un caractère minuscule.

* **TrackState (winJS: trackState)**

   Contrôle l’état d’une application avec les données contextuelles facultatives. Les états sont les vues disponibles dans votre application, telles que &quot;tableau de bord d’accueil&quot;, &quot;paramètres de l’application&quot;, &quot;panier&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `TrackState` incrémentent les pages vues. Si `state` est vide, il s’affiche sous la forme &quot;nom d’application version d’application (compilation)&quot; dans les rapports. Si cette valeur apparaît dans les rapports, veillez à définir `state` dans chaque appel `TrackState`.

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

* **TrackAction (winJS: trackAction)**

   Effectue le suivi d’une action dans votre application. Les actions sont les actions qui se produisent dans votre application et que vous souhaitez mesurer, telles que les &quot;connexions&quot;, les &quot;clics sur la bannière&quot;, les &quot;abonnements de flux&quot; et d’autres mesures.

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

   envoie l’identifiant visiteur automatiquement généré pour Analytics. Il s’agit d’un identifiant de visiteur unique propre à l’application, qui est généré au lancement initial, puis stocké et utilisé à partir de ce moment. Cet identifiant est conservé entre les mises à niveau de l’application et supprimé lors de la désinstallation.

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

   Commence une minutée portant le nom `action` action. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

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

   Transmet `contextData` afin de mettre à jour les données contextuelles associées à l’`action` donnée. Le `data` transmis est ajouté aux données existantes pour l&#39;action donnée et remplace les données si la même clé est déjà définie pour `action`.

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

   Renvoie true si l’action minutée donnée existe et false dans le cas contraire.

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

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Efface tous les accès stockés de la file d’attente de suivi Analytics.

   * Voici la syntaxe de ce message :

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

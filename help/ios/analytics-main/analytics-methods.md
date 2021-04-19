---
description: Cette section répertorie les méthodes Adobe Analytics fournies par la bibliothèque iOS.
seo-description: Cette section répertorie les méthodes Adobe Analytics fournies par la bibliothèque iOS.
seo-title: Méthodes Analytics
solution: Experience Cloud,Analytics
title: Méthodes Analytics
topic-fix: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
exl-id: 327ec44a-be15-47af-a2c8-a373124999ad
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---

# Méthodes Analytics {#analytics-methods}

Cette section répertorie les méthodes Adobe Analytics fournies par la bibliothèque iOS.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform. Un préfixe est attribué aux méthodes selon la solution. Les méthodes Experience Cloud ID sont précédées du préfixe `track`.

Chacune de ces méthodes est utilisée pour envoyer des données dans la suite de rapports Adobe Analytics.

* **trackState:&#x200B;data:**

   Les états sont les affichages disponibles dans l’application, par exemple `home dashboard`, `app settings`, `cart`, etc. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues. Si `state` est vide, il est présenté comme *app name app version (build)* dans les rapports. Si vous voyez cette valeur dans les rapports, veillez à définir `state` dans chaque appel `trackState`.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   Effectue le suivi d’une action dans votre application. Actions que vous voulez mesurer, par exemple `logons`, `banner taps`, `feed subscriptions`, et autres mesures, qui se produisent dans l’application.

   >[!TIP]
   >
   >Si vous avez du code qui peut s’exécuter pendant que l’application est en arrière-plan (par exemple, une récupération de données en arrière-plan), utilisez plutôt `trackActionFromBackground`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Récupère l’identifiant de suivi des analyses.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   Effectue le suivi d’une action survenue en arrière-plan, ce qui empêche les événements de cycle de vie de se déclencher dans certains scénarios.

   >[!TIP]
   >
   >Invoquez cette méthode uniquement dans le code qui s’exécute pendant que l’application est en arrière-plan.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   Envoie les coordonnées x et y actuelles. Utilise en outre les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   Effectue un suivi quand un utilisateur entre à proximité d’une balise.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Efface les données de balise une fois qu’un utilisateur n’est plus à proximité de la balise.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   Commence une minutée portant le nom `action` action. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   Transmet `data` afin de mettre à jour les données contextuelles associées à l’`action` donnée. Les données `data` transmises sont ajoutées aux données existantes pour l’action et, si la même clé est déjà définie pour `action`, écrase les données.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   Termine une action minutée. Si vous fournissez un `block`, vous pourrez accéder aux valeurs de délai final et manipuler `data` avant d’envoyer l’accès final.

   >[!TIP]
   >
   >Si vous fournissez un `block`, vous devez renvoyer `YES` (OUI) pour envoyer un accès. Le transfert de `nil` pour `block` envoie l’accès final.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Renvoie si une action minutée est ou non en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Requiert le SDK 4.1. Quel que soit le nombre d’accès déjà en file d’attente, permet de forcer la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Récupère le nombre d’accès actuellement dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   >[!CAUTION]
   >
   >Soyez prudent lorsque vous effacez manuellement la file d’attente. Cette action est irréversible.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Effectue le suivi d’un clic publicitaire de message push.

   >[!IMPORTANT]
   >
   >Cette méthode n’incrémente pas les pages vues.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```

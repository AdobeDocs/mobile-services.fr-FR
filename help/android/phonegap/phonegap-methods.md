---
description: Vous pouvez utiliser les méthodes du module externe PhoneGap iOS pour réaliser différentes tâches.
keywords: android ; library ; mobile ; sdk
seo-description: Vous pouvez utiliser les méthodes du module externe PhoneGap iOS pour réaliser différentes tâches.
seo-title: Méthodes du module phonegap
solution: Marketing Cloud, Analytics
title: Méthodes du module phonegap
topic: Développeur et mise en œuvre
uuid: bc 3 db 9 ce -81 b 7-45 ec -88 aa -6020 c 1 db 5 d 9 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Vous pouvez utiliser les méthodes du module externe Android PhoneGap pour réaliser diverses tâches.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Renvoie l’état de confidentialité pour l’utilisateur actuel.

   Vous trouverez ci-dessous les états disponibles :

   * `ADB.optedIn`: Les accès sont envoyés immédiatement.
   * `ADB.optedOut`: Les accès sont ignorés.
   * `ADB.optUnknown`: Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés). **** Si la suite de rapports **ne prend pas** en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.

   * Voici l’exemple de code pour cette méthode :

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`.

   Vous pouvez définir l’un des états suivants :

   * `ADB.optedIn`: Les accès sont envoyés immédiatement.
   * `ADB.optedOut`: Les accès sont ignorés.
   * `ADB.optUnknown`: Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés). **** Si la suite de rapports **ne prend pas** en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est 0.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. Par défaut, cette variable est définie sur `false`.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtient la version de la bibliothèque.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Renvoie l’identifiant visiteur généré automatiquement.

   Il s’agit d’un identifiant visiteur unique, spécifique à une application, généré au lancement initial de l’application, puis stocké et utilisé à partir de ce lancement. Cet identifiant est conservé d’une mise à niveau à l’autre, puis est supprimé lorsque l’application est désinstallée.

   >[!TIP]
   >
   >Si votre application est mise à niveau depuis le SDK Experience Cloud 3. x vers 4. x, l'identifiant visiteur précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu'identificateur d'utilisateur personnalisé. Pour plus d’informations, voir `getUserIdentifier` ci-dessous. Cet identifiant conserve les données des visiteurs d’une mise à niveau à l’autre du SDK.

   Pour les nouvelles installations sur le SDK 4.x, l’identifiant de l’utilisateur a la valeur `null` et l’identifiant de suivi est utilisé.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Si un identifiant utilisateur de client a été défini, renvoie cet identifiant ; si l’identifiant n’a pas été défini, renvoie la valeur `null`. La valeur par défaut est `null`.

   * Voici l’exemple de code pour cette méthode :

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Définit le jeton d’appareil pour les notifications Push.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Définit la préférence d’une session de cycle de vie persistante.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Utilisez cette méthode seulement si votre application est enregistrée pour les notifications en arrière-plan.

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Force la bibliothèque à envoyer tous les accès mis en file d’attente, quelles que soient les options de lot en cours.

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtient ou définit le nombre d’appels de suivi stockés dans la file d’attente hors ligne.

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Supprime tous les appels de suivi stockés de la file d’attente hors ligne.

   >[!WARNING]
   >
   >Soyez prudent lorsque vous effacez manuellement la file d'attente, car elle ne peut pas être annulée.

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envoie une demande de collecte PII.

   * Voici la syntaxe de cette méthode :
   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Effectue le suivi d’un clic publicitaire de lien profond Adobe.

   >[!TIP]
   >
   >Si l'appel de cycle de vie est un événement de lancement, les données Adobe Link sont annexées ; sinon un appel supplémentaire est envoyé.

   * Voici la syntaxe de cette méthode :

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

   `cData`: objet JSON avec des paires clé-valeur à envoyer dans les données contextuelles.

   * Voici la syntaxe de cette méthode :

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Voici quelques exemples de code pour cette méthode :

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Effectue le suivi d’une action dans votre application. Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * Voici la syntaxe de cette méthode :

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Envoie les coordonnées x et y actuelles. Utilise également les points ciblés définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   Commence une minutée par le nom `action`action.

   Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   Les données `cData` transmises sont ajoutées aux données existantes pour l’action et, si la même clé est déjà définie pour `action`, écrase les données.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   Termine une action minutée.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Renvoie si une action minutée est ou non en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Effectue un suivi quand un utilisateur entre à proximité d’une balise.

   * Voici la syntaxe de cette méthode :

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Efface les données de balise une fois qu’un utilisateur n’est plus à proximité de la balise.

   * Voici la syntaxe de cette méthode :

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Méthodes Target {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Envoie une demande au serveur `Target` configuré et renvoie la valeur de chaîne de l’offre.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envoie une demande au serveur `Target` configuré.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Efface les cookies `Target` du stockage des cookies partagé.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Obtient la valeur du cookie `SessionID` renvoyée pour ce visiteur par le serveur Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Obtient la valeur du cookie `PcID` renvoyée pour le visiteur par le serveur `Target`.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Définit l’identifiant visiteur personnalisé pour Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Obtient l’identifiant visiteur personnalisé pour Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Voici un exemple de code pour cette méthode :

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Envoie une demande au serveur Target configuré et renvoie la valeur de chaîne de l’offre.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. Pour plus d'informations, voir [Méthodes de configuration](/help/android/configuration/methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtient le profil du visiteur.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   Renvoie le DPUUID.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   Renvoie le DPID.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Définit les DPID et DPUUID.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Traite une demande de service Audience Manager.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   UUID Audience Manager et purge le profil du visiteur actuel.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Renvoie l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   Synchronise les identifiants fournis avec le service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Synchronise les identifiants fournis au service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   Synchronise l’identifiant fourni au service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   Ajoute les identifiants visiteur à l’URL donnée.

   * Voici la syntaxe de cette méthode :

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
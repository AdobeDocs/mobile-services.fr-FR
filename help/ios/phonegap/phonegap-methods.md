---
description: Vous pouvez utiliser les méthodes du module externe PhoneGap iOS pour réaliser différentes tâches.
keywords: phonegap
seo-description: Vous pouvez utiliser les méthodes du module externe PhoneGap iOS pour réaliser différentes tâches.
seo-title: Méthodes du module PhoneGap
solution: Marketing Cloud, Analytics
title: Méthodes du module PhoneGap
topic: Développeur et mise en œuvre
uuid: bd 830 fe 5-804 a -4 d 0 a-bbb 6-99 a 6 d 8 da 6 a 03
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods {#phonegap-plug-in-methods}

Vous pouvez utiliser les méthodes du module externe PhoneGap iOS pour réaliser différentes tâches.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Renvoie l’état de confidentialité pour l’utilisateur actuel. Vous trouverez ci-dessous les états disponibles :

   * `ADB.optedIn` : les accès sont envoyés immédiatement.
   * `ADB.optedOut`, où les accès sont ignorés.
   * `ADB.optUnknown`Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés). **** Si la suite de rapports **ne prend pas** en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».\
      La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.

      * Voici l’exemple de code pour cette méthode :

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   Définit l’état de confidentialité pour l’utilisateur actuel sur `status`. Vous pouvez définir l’un des états suivants :
   * `ADB.optedIn` : les accès sont envoyés immédiatement.
   * `ADB.optedOut`, où les accès sont ignorés.
   * `ADB.optUnknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés).****

      Si la suite de rapports **ne prend pas** en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

   * Voici l’exemple de code pour cette méthode :

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est 0.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. Par défaut, cette variable est définie sur `false`.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtient la version de la bibliothèque.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Renvoie l’identifiant visiteur généré automatiquement. Il s’agit d’un identifiant visiteur unique spécifique à une application généré au lancement initial de l’application, puis stocké et utilisé à partir de ce lancement. Cet identifiant est conservé d’une mise à niveau de l’application à l’autre, puis est supprimé à la désinstallation de l’application.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous visitor ID (custom or automatically generated) is retrieved and stored as the custom user identifier (see `getUserIdentifier` below). Cela permet de conserver les données du visiteur entre les mises à niveau du SDK. For new installations on the 4.x SDK, the user identifier is `null`, and tracking identifier is used.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Renvoie l’identifiant d’utilisateur personnalisé si un identifiant personnalisé a été défini, puis renvoie la valeur `null` si aucun identifiant personnalisé n’a été défini. La valeur par défaut est `null`.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Définit l’identifiant d’utilisateur sur `identifier`.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Définit le jeton d’appareil pour les notifications Push.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Définit la préférence d’une session de cycle de vie persistante.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Utilisez cette méthode seulement si votre application est enregistrée pour les notifications en arrière-plan.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Force la bibliothèque à envoyer tous les accès mis en file d’attente, quelles que soient les options de lot en cours.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtient ou définit le nombre d’appels de suivi stockés dans la file d’attente hors ligne.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Supprime tous les appels de suivi stockés de la file d’attente hors ligne.

   >[!CAUTION]
   >
   >faites attention lorsque vous effacez manuellement la file d'attente, car cette opération ne peut pas être annulée.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Indique au SDK que la prochaine reprise depuis l’arrière-plan ne doit pas commencer une nouvelle session, quelle que soit la valeur de temporisation de la session du cycle de vie dans le fichier de configuration.

   >[!IMPORTANT]
   >
   >Important : Cette méthode est conçue pour les applications qui s’inscrivent aux notifications quand elles sont en arrière-plan et doit être appelée uniquement depuis votre code qui s’exécute pendant que votre application se trouve en arrière-plan.

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   Indique au SDK que les données du cycle de vie doivent être collectées pour être utilisées à l’échelle de toutes les solutions dans le SDK. For more information, see [Lifecycle metrics](/help/ios/metrics.md).

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envoie une demande de collecte PII.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Effectue le suivi d’un clic publicitaire de lien profond Adobe.

   >[!TIP]
   >
   >Si l'appel de cycle de vie est un événement de lancement, les données Adobe Link sont annexées ; sinon un appel supplémentaire est envoyé.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Effectue le suivi d’un clic publicitaire de message push.

   * Voici la syntaxe de cette méthode :

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Effectue le suivi d’un clic publicitaire de message de notification locale.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Contrôle l’état d’une application avec les données contextuelles facultatives. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues. Cdata est un objet JSON avec des paires clé-valeur à envoyer dans des données contextuelles.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Effectue le suivi d’une action dans votre application. Actions are the things that happen in your app that you want to measure, include `logins`, `banner taps`, `feed subscriptions` and other metrics.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Voici les exemples de code pour cette méthode :

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Effectue le suivi d’une action survenue en arrière-plan. Ceci empêche les événements de cycle de vie de se déclencher dans certains scénarios.

   * Voici la syntaxe de cette méthode :

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Voici les exemples de code pour cette méthode :

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Envoie les coordonnées x et y actuelles. Also uses the points of interest that were defined in the `ADBMobileConfig.json` file to determine if the location provided as a parameter is within any of your POIs. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Ajoute `amount` à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   Commence une minutée portant le nom `action`action. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Transmet `cData` afin de mettre à jour les données contextuelles associées à l’`action` donnée. Les `cData` (données) transmises sont ajoutées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’`action`.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Méthodes Target {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Envoie la demande à votre serveur `Target` configuré et renvoie la valeur de chaîne de l’offre.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envoie une demande au serveur Target configuré.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Efface les cookies Target du stockage des cookies partagé.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Traite une demande de service Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Traite une demande de service Target.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Obtient la valeur du cookie `PcID` renvoyée pour ce visiteur par le serveur Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Définit l’identifiant visiteur personnalisé pour Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Voici l'exemple de code de ce groupe :

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Obtient l’identifiant visiteur personnalisé pour Target.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Permet aux développeurs de lancer une campagne d’acquisition d’applications, comme si l’utilisateur avait cliqué sur un lien. Ceci s’avère utile pour créer des liens d’acquisition manuels et pour gérer vous-même les redirections de boutiques d’applications (comme avec un `SKStoreView`).

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the `AppDelegate` generated by Cordova, call `[ADBMobile setAdvertisingIdentifier:]` in the `application:didFinishLaunchingWithOptions:` delegate method. Pour plus d'informations, voir [Méthodes de configuration](/help/ios/configuration/sdk-methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtient le profil du visiteur.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   Renvoie le DPUUID.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   Renvoie le DPID.

   * Voici la syntaxe de cette méthode :

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Définit les DPID et DPUUID.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Traite une demande de service Audience Manager.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Réinitialise l’UUID du gestionnaire d’audience et purge le profil du visiteur en cours.

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.audienceReset(); 
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Renvoie l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   Synchronise les identifiants fournis avec le service d’identification.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Voici les exemples de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Synchronise les identifiants fournis avec le service d’identification des visiteurs.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   Synchronise l’identifiant fourni avec le service d’identification des visiteurs.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   Ajoute les identifiants visiteur à l’URL donnée.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Renvoie tous les `visitorIDs` qui ont été synchronisés.

   * Voici la syntaxe de cette méthode :

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```


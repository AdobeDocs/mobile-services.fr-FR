---
description: Cette section répertorie les méthodes TVJS fournies par la bibliothèque tvOS.
seo-description: Cette section répertorie les méthodes TVJS fournies par la bibliothèque tvOS.
seo-title: Méthodes TVJS
solution: Experience Cloud,Analytics
title: Méthodes TVJS
topic: Développeur et mise en œuvre
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Méthodes TVJS {#tvjs-methods}

Cette section répertorie les méthodes TVJS fournies par la bibliothèque tvOS.

## Méthodes de configuration{#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Renvoie la version actuelle de la bibliothèque Adobe Mobile.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      version()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Retours : `String`

* **privacyStatus**

   Renvoie la représentation NSUInteger de l’état de confidentialité pour l’utilisateur actuel.

   Options disponibles :

   * `ADBMobilePrivacyStatusOptIn` : les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` : les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : Si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).

      Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion. La valeur par défaut est définie dans le fichier `ADBMobileConfig.json`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      privacyStatus()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Retours : `Number`

* **setPrivacyStatus**

   Définit l’état de confidentialité de l’utilisateur actuel sur l’une des valeurs suivantes :

   * `ADBMobilePrivacyStatusOptIn` : les accès sont immédiatement envoyés.
   * `ADBMobilePrivacyStatusOptOut` : les accès sont ignorés.
   * `ADBMobilePrivacyStatusUnknown` : Si le suivi hors ligne est activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).
   Si le suivi hors ligne n’est pas activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Renvoie la valeur du cycle de vie de l’utilisateur actuel. La valeur par défaut est `0`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      lifetimeValue()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Retours : `Number`

* **userIdentifier**

   Renvoie l’identifiant d’utilisateur si un identifiant personnalisé a été défini. Renvoie une valeur nil si aucun identifiant personnalisé n’est défini. La valeur par défaut est de `nil`

   >[!IMPORTANT]
   >
   >Si votre application est mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’identifiant visiteur précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Ceci permet de conserver les données visiteur entre les différentes mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant utilisateur est nil tant qu’il n’a pas été défini.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      userIdentifier()
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Retours : `String`

* **setUserIdentifier**

   Définit l’identifiant d’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Renvoie : S/O

   * Paramètre :  `userID`

      * Type : String
      * Nouvel identifiant pour cet utilisateur.

* **setAdvertisingIdentifier**

   Définit l’IDFA dans le SDK et, s’il a été défini dans le SDK, l’IDFA est envoyé dans le cycle de vie. L’IDFA est également accessible dans Signals (Postbacks).

   >[!IMPORTANT]
   >
   >Vous devez récupérer l’IDFA d’API Apple uniquement si vous utilisez un service publicitaire. Si vous récupérez l’IDFA, mais ne l’utilisez pas correctement, il est possible que votre application soit rejetée.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Renvoie : S/O
   * Paramètre : `idfa`
      * Type : `String`
      * IDFA récupéré d’un API Apple.

* **setDebugLogging**

   Définit la préférence de journalisation de débogage.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      setDebugLogging(logging)
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Renvoie : S/O
   * Paramètres : `logging`
      * Type : `Bool`
      * Valeur indiquant si le SDK Adobe doit se connecter à la console de débogage.


## Méthodes Analytics{#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Contrôle l’état d’une application avec les données contextuelles facultatives. Les états correspondent aux affichages disponibles dans votre application : tableau de bord d’accueil, paramètres d’application, panier, etc. Ces états sont semblables aux pages d’un site web ; les appels trackState incrémentent les pages vues.

   Si l’état est vide, il est présenté comme app name app version (build) dans les rapports. Si vous voyez cette valeur dans les rapports, veillez à définir l’état dans chaque appel trackState.

   >[!TIP]
   >
   >Il s’agit du seul appel de suivi qui incrémente les pages vues.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Renvoie : S/O
      * Paramètre : `stateName`
         * Type : `String`
         * Nom d’état de la page
      * Paramètre : `contextData`
         * Type : Object
         * Données contextuelles supplémentaires pour cet accès.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Effectue le suivi d’une action dans votre application. Les actions sont les événements qui se produisent dans votre application et que vous souhaitez mesurer, par exemple les connexions, les appuis sur la bannière, les abonnements aux flux, etc.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Renvoie : S/O
      * Paramètres : `actionName`
         * Type : String
         * Nom de l’action suivie.
      * Paramètre : `contextData`
         * Type : Object
         * Données contextuelles supplémentaires pour cet accès.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Envoie les coordonnées de latitude et de longitude actuelles.

   Utilise en outre les points ciblés (POI) définis dans le fichier `ADBMobileConfig.json` pour déterminer si l’emplacement fourni comme paramètre se trouve dans l’un de vos points ciblés. Si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Renvoie : S/O
      * Paramètre : `lat`
         * Type : nombre
         * Latitude de l’emplacement.
      * Paramètre : `lon`
         * Type : nombre
         * Longitude de l’emplacement.
      * Paramètre : `contextData`
         * Type : Object
         * Données contextuelles supplémentaires pour cet accès.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Ajoute une quantité à la valeur de durée de vie de l’utilisateur.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Renvoie : S/O
      * Paramètre : `increaseAmount`
         * Type : nombre
         * Quantité à ajouter à la valeur de durée de vie de l’utilisateur actuel.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Commence une action minutée par l’action du nom. Si vous appelez cette méthode pour une action qui a déjà commencé, l’action minutée précédente est écrasée.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Renvoie : S/O
      * Paramètre : `name`
         * Type : String
         * Nom de l’action minutée lancée.
      * Paramètre : `contextData`
         * Type : Object
         * Données contextuelles supplémentaires pour cet accès.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Transmet des données afin de mettre à jour les données contextuelles associées à l’action donnée.

   Les données transmises sont annexées aux données existantes pour l’action donnée et remplacent les données si la même clé est déjà définie pour l’action.

   >[!TIP]
   >
   >Cet appel n’envoie pas d’accès.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Renvoie : S/O
      * Paramètre : `name`
         * Type : String
         * Nom de l’action minutée mise à jour.
      * Paramètre : `contextData`
         * Type : Object
         * Données contextuelles supplémentaires pour cet accès.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Termine une action minutée.

   Si vous spécifiez une fonction de rappel, vous pouvez accéder aux valeurs temporelles finales. Si aucun rappel n’est spécifié ou si le rappel renvoie « true », le SDK Adobe envoie automatiquement un accès. Lorsque que false est renvoyé par le rappel, l’accès de l’action minutée est supprimé.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Renvoie : S/O
      * Paramètres : `name`
         * Type : String
         * Nom de l’action minutée terminée.
      * Paramètre : `callback`
         * Type : `function(inAppDuration, totalDuration, data)`
         * Méthode de rappel qui aura `inAppDuration` (nombre), `totalDuration` (nombre), et `data` (objet de données contextuelles) dans ses paramètres.

            Vous pouvez empêcher l’envoi de l’accès final par le SDK en renvoyant `false` dans votre fonction de rappel.
      * Voici l’exemple de code pour cette méthode :

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Renvoie si une action minutée est ou non en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Renvoie : Bool
      * Paramètre : `name`
         * Type : `String`
         * Nom de l’action minutée pour laquelle vous devez vérifier l’existence.
   * Voici l’exemple de code pour cette méthode :


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Renvoie l’identifiant visiteur généré automatiquement.

   Il s’agit d’un identifiant visiteur unique propre à l’application qui est généré par les serveurs d’Adobe. Si les serveurs d’Adobe ne sont pas joignables au moment de la génération, l’identifiant est généré au moyen du CFUUID d’Apple. La valeur est générée au lancement initial, puis stockée et utilisée à partir de ce point. Cet identifiant est conservé entre les différentes mises à jour de l’application, enregistré et restauré au cours du processus standard de sauvegarde de l’application, puis supprimé lorsque l’application est désinstallée.

   >[!TIP]
   >
   >Si votre application est mise à niveau du SDK Experience Cloud 3.x vers 4.x, l’identifiant visiteur précédent (personnalisé ou généré automatiquement) est récupéré et stocké en tant qu’identifiant utilisateur personnalisé. Ceci permet de conserver les données visiteur entre les différentes mises à niveau du SDK. Pour les nouvelles installations sur le SDK 4.x, l’identifiant utilisateur est `nil` et l’identifiant de suivi est utilisé. Pour plus d’informations, voir la ligne userIdentifier ci-dessous.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackingIdentifier()
      ```

      * Retours : `String`
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Force la bibliothèque à envoyer tous les accès dans la file d’attente hors ligne, peu importe le nombre d’accès déjà dans la file d’attente.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Renvoie : S/O
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Efface tous les accès de la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackingClearQueue()
      ```

      * Renvoie : S/O
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Récupère le nombre d’accès actuellement dans la file d’attente hors ligne.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      trackingGetQueueSize()
      ```

      * Renvoie : nombre
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Méthodes Audience Manager{#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Renvoie le dernier profil du visiteur obtenu.

   Renvoie null si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `NSUserDefaults` pour un accès facile à l’échelle de plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      audienceVisitorProfile()
      ```

      * Renvoie : objet
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   Renvoie le DPID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      audienceDpid()
      ```

      * Renvoie : String
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   Renvoie le DPUUID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      audienceDpuuid()
      ```

      * Retours : `String`
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   Définit le dpid et le dpuuid qui, une fois définis, sont envoyés avec chaque signal.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Renvoie : S/O
      * Paramètre : `dpid`
         * Type : `String`
         * Identifiant du fournisseur de données Audience Manager.
      * Paramètre : `dpuuid`
         * Type : `String`
         * Identifiant pour la combinaison utilisateur / fournisseur de données.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Envoie à Audience Manager un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Paramètre : `traits`
         * Type : Object
         * Dictionnaire des caractéristiques pour cet utilisateur.
      * Paramètre : `callback`
         * Type : function(profile)
         * Profil renvoyé depuis Audience Manager dans le paramètre de la fonction de rappel.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Réinitialise l’UUID d’Audience Manager et purge le profil du visiteur actuel.

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      audienceReset()
      ```

      * Renvoie : S/O
      * Paramètre : Aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.audienceReset();
      ```


## Méthodes du service d’identification {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Récupère l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Renvoie : String
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Outre l’Experience Cloud ID, vous pouvez définir d’autres identifiants de client à associer à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour un même visiteur, ainsi qu’un identifiant de type client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants setCustomerID dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Renvoie : S/O
      * Paramètre : `identifiers`

         * Type : `Object`
         * Identifiants à synchroniser avec le service d’identification pour cet utilisateur.
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   Synchronise les identifiants fournis au service d’identification.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Renvoie : S/O
      * Paramètres : `identifiers`
         * Type : `Object`
         * Identifiants à synchroniser avec le service d’identification pour cet utilisateur.
      * Paramètre : `authState`
         * Type : ADBMobileVisitorAuthenticationState
         * État d’authentification de l’utilisateur et valeurs possibles :
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   Synchronise le type d’identifiant et la valeur fournis au service d’identification.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Renvoie : S/O
      * Paramètre : `idType`
         * Type : `String`
         * Type d’identifiant que vous synchronisez.
      * Paramètre : `identifier`
         * Type : `String`
         * Valeur de l’identifiant que vous synchronisez.
      * Paramètre : `authState`
         * Type : ADBMobileVisitorAuthenticationState
État d’authentification de l’utilisateur. Valeurs possibles :
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   Récupère une matrice d’objets ADBVisitorID en lecture seule. Le code ci-après est un exemple d’objet VisitorID :

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Voici la syntaxe de cette méthode :

      ```objective-c
      visitorGetIDsJs()
      ```

      * Retours : `Array [Object]`

      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Méthodes Target {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Renvoie l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      targetThirdPartyID()
      ```

      * Retours : `String`
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Définit l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Renvoie : S/O
      * Paramètres : `thirdPartyID`
         * Type : `String`
         * Identifiant tiers à utiliser pour les demandes cibles.
   * Voici l’exemple de code pour cette méthode :
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Renvoie le PcID.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      targetPcID()
      ```

      * Retours : `String`
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Renvoie l’ID de session.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      targetSessionID()
      ```

      * Retours : `String`
      * Paramètres : aucun
   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```

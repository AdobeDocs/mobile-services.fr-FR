---
description: Ces informations vous aideront à utiliser le fichier de configuration ADBMobile.json.
solution: Experience Cloud Services,Analytics
title: Fichier de configuration JSON ADBMobile
topic-fix: Developer and implementation
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
exl-id: 652aeb05-b052-448d-98c8-d513d050a6f5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 100%

---

# Fichier de configuration ADBMobile JSON {#adbmobile-json-config}

Ces informations vous aident à comprendre les variables du fichier de configuration ADBMobile.json.

## `ADBMobileConfig.json` Référence du fichier de configuration {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Vous pouvez utiliser le même fichier de configuration pour votre application sur différentes plateformes :

>[!TIP]
>
>Sur **Android**, vous devez placer le fichier `ADBMobileConfig.json` dans le dossier `assets`.

Voici la liste des variables du fichier JSON et la version minimale du SDK dont vous avez besoin pour chaque variable :

* **acquisition**
   * Version minimale du SDK : 4.1
   * Permet l’acquisition des applications mobiles.
      * `server` : serveur d’acquisition vérifié lors du lancement initial pour un référent d’acquisition.
      * `appid` : ID généré qui identifie de manière unique cette application sur le serveur d’acquisition.

   Si cette section manque, activez l’acquisition de l’application mobile et téléchargez à nouveau le fichier de configuration du SDK. Pour plus d’informations, voir *referrerTimeout* dans cette liste de variables.

* **analyticsForwardingEnabled**
   * Version minimale du SDK : 4.8.0.
   * La valeur par défaut est `false`.

      Propriété dans l’objet `audienceManager`. Si Audience Manager est configuré et `analyticsForwardingEnabled` est défini sur `true`, tout le trafic Analytics est également transféré vers Audience Manager.

* **backdateSessionInfo**
   * Version minimale du SDK : 4.6.
   * Active/désactive la capacité pour le SDK Adobe d’antidater les accès aux informations de session.

      Les accès aux informations de session comprennent actuellement les blocages et la durée de session et peuvent être activés ou désactivés.

      **Activation ou désactivation des accès**

      * Si vous définissez la valeur sur `false`, les accès sont **désactivés**. Le SDK reprend le même comportement qu’avant la version 4.1, ce qui consiste à regrouper les informations de session de la session précédente avec le premier accès de la session suivante. Le SDK Adobe associe également les informations de session au cycle de vie actuel, ce qui évite la création d’une visite exagérée. Comme les visites exagérées ne sont plus créées, le nombre de visites diminue immédiatement.

      * Si vous ne spécifiez aucune valeur, la valeur par défaut est `true` et les accès sont **activés**. Lorsque les accès sont activés, le SDK Adobe antidate l’accès aux informations de session à 1 seconde après l’accès final de la session précédente. Cela signifie que les données de blocage et de session seront corrélées avec la date correcte à laquelle elles se sont produites. Un effet secondaire est que le SDK peut créer une visite pour l’accès antidaté. Une correspondance subit un effet rétroactif à chaque nouveau lancement de l’application.

         >[!IMPORTANT]
         >
         >Les informations d’accès aux sessions antidatées sont envoyées dans un appel de serveur d’informations de session et des appels de serveur supplémentaires peuvent être requis.

* **batchLimit**
   * Version minimale du SDK : 4.1
   * Nombre limite d’accès pouvant faire l’objet d’appels consécutifs.

      Si, par exemple, `batchLimit` est défini sur 10, chaque accès précédant le 10e accès est placé en file d’attente. Lorsque le 10e accès intervient, les 10 accès sont tous envoyés consécutivement.

      À noter :

      * La valeur par défaut est `0`, ce qui signifie que le traitement par lot n’est pas activé.
      * Nécessite `offlineEnabled = true`.

* **charset**
   * Version minimale du SDK : 4.0
   * Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics.

      La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports.

* **clientCode**
   * Version minimale du SDK : 4.0
   * Code client qui vous a été attribué.

      >[!IMPORTANT]
      >
      >Cette variable est requise par Target.

* **coopUnsafe**
   * Version minimale du SDK : 4.16.1
   * Propriété booléenne de l’objet `marketingCloud` qui, lorsqu’elle est définie sur `true`, entraîne l’exclusion du périphérique de la solution Device Co-op d’Experience Cloud.
   * La valeur par défaut est `false`.
   * Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.

   Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste de blocage sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

   À noter :

   * Si `coopUnsafe` est défini sur `true`, `coop_unsafe=1` sera toujours annexé aux accès Audience Manager et identifiants visiteur.
   * Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.


* **environmentId**
   * Version minimale du SDK : 4.14
   * Identifiant de l’environnement que vous souhaitez utiliser.

      Vous pouvez spécifier un identifiant valide (`environmentId=8`) et, si `environmentId` n’est pas inclus, l’environnement de production par défaut est utilisé.

* **lifecycleTimeout**
   * Version minimale du SDK : 4.0
   * La valeur par défaut est de 300 secondes.

      Spécifie la durée, en secondes, qui doit s’écouler entre le lancement de l’application et le moment où le lancement est considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque votre application est envoyée en arrière-plan et réactivée.

      Le temps passé par votre application en arrière-plan n’est pas inclus dans la durée de session.

* **messages**

   * Version minimale du SDK : 4.2
   * Généré automatiquement par Adobe Mobile Services, définit les paramètres de la messagerie in-app. Pour plus d’informations, consultez la section *Description des messages* ci-dessous.

* **offlineEnabled**

   * Version minimale du SDK : 4.0
   * Lorsque cette variable est activée, les accès sont placés en file d’attente pendant que l’appareil est hors ligne et envoyés ultérieurement quand l’appareil est en ligne.

      La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

      La valeur par défaut est `false`.

      >[!IMPORTANT]
      >
      >Si les horodatages sont activés sur votre suite de rapports, votre propriété de configuration `offlineEnabled` **doit** être définie sur « true ». Si la suite de rapports n’est pas horodatée, la propriété de configuration `offlineEnabled` **doit** être définie sur « false ».
      >
      >En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si l’horodatage d’une suite de rapports est activé,  contactez l’Assistance clientèle ou téléchargez le fichier de configuration depuis Adobe Mobile Services.

      Si vous collectez actuellement des données AppMeasurement dans une suite de rapports qui collecte également des données de JavaScript, il est possible que vous deviez configurer une suite de rapports distincte pour les données mobiles ou que vous deviez inclure un horodatage personnalisé pour tous les accès JavaScript à l’aide de la variable `s.timestamp`.

* **org**

   * Version minimale du SDK : 4.3
   * Indique l’ID d’organisation Experience Cloud pour le service d’identification.

* **poi**
   * Version minimale du SDK : 4.0
   * Chaque matrice de point ciblé (POI) contient le nom du point ciblé, sa latitude, sa longitude et son rayon (en mètres) pour la zone du point.

      Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé, si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      À partir de la version 4.2, les points ciblés sont définis dans l’interface Adobe Mobile et synchronisés dynamiquement avec les fichiers de configuration de l’application. Cette synchronisation requiert le paramètre `analytics.poi` :

      ```javascript
        "analytics.poi": `https://assets.adobedtm.com/`
      …/yourfile.json"`,
      ```

      Si ce paramètre n’est pas configuré, le fichier `ADBMobile.json` doit être mis à jour afin d’inclure cette ligne. Pour télécharger un fichier de configuration mis à jour, voir [Avant de démarrer](/help/android/getting-started/requirements.md).

* **postback**
   * Version minimale du SDK : 4.6
   * Voici la définition du modèle de message « callback » :

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      L’objet `payload` du code est un exemple de charge utile pour une définition de message qui va dans le fichier `ADBMobileConfig.json`. Pour en savoir plus, consultez la rubrique [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * Version minimale du SDK : 4.0
   * La valeur par défaut est `optedin`.
      * Pour `optedin`, les accès sont envoyés immédiatement.
      * Pour `optedout`, les accès sont ignorés.
      * Pour `optunknown`, si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés).

      Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur `optedin`.  Cela ne définit que la valeur initiale. Si cette valeur est définie ou modifiée dans le code, la nouvelle valeur est utilisée jusqu’à ce qu’elle soit à nouveau modifiée, ou lorsque l’application est désinstallée et réinstallée.


* **referrerTimeout**
   * Version minimale du SDK : 4.1
   * Nombre de secondes pendant lesquelles le SDK attend les données du référent d’acquisition lors du lancement initial avant d’expirer. Si vous utilisez l’acquisition, nous vous recommandons un délai d’attente de 5 secondes.

      >[!IMPORTANT]
      >
      >Cette variable est requise par Acquisition. Si la variable est définie sur `0` ou n’est pas incluse, le SDK n’attend pas les données d’acquisition et le suivi des mesures d’acquisition n’est pas effectué.

* **remotes**
   * Version minimale du SDK : 4.2
   * Configurée automatiquement et définit les points de terminaison hébergés par Adobe pour les fichiers de configuration dynamiques.

      L’heure de la dernière mise à jour de chaque fichier de configuration est comparée à la version en cours à chaque lancement ; les mises à jour sont téléchargées et enregistrées.
      * `analytics.poi` est le point de terminaison de la configuration des points ciblés hébergés.
      * `messages` est le point de terminaison de la configuration des messages in-app hébergés.

* **rsids**
   * Version minimale du SDK : 4.0
   * Une ou plusieurs suites de rapports pour recevoir des données Analytics. Plusieurs ID de suite de rapports doivent être séparés par des virgules sans espace entre eux.

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Cette variable est requise par Analytics.

* **server**
   * Version minimale du SDK : 4.0
   * Serveur Analytics ou de la gestion de l’audience, en fonction du nœud parent. Cette variable doit être renseignée par le domaine du serveur, sans préfixe de protocole `https://` ou `https://`. Ce préfixe est géré automatiquement par la bibliothèque en fonction de la variable `ssl`. Si `ssl` est `true`défini sur, une connexion sécurisée est établie avec le serveur. Si `ssl` est `false`défini sur, une connexion non sécurisée est établie avec le serveur.

* **ssl**
   * Version minimale du SDK : 4.0
   * La valeur par défaut est `false`.

      Active (`true`) ou désactive (`false`) la fonctionnalité d’envoi des données de mesure en utilisant SSL (HTTPS).

      La définition du modèle de message « callback » est présentée ci-dessous :

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * Version minimale du SDK : 4.0
   * Détermine le délai pendant lequel Target attend une réponse.


## Exemple de fichier `ADBMobileConfig.json` :  {#section_4655EF79744649E5A5AE19E3224C472C}

Voici un exemple de fichier `ADBMobileConfig.json` :

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## Description des messages {#section_B97D654BA92149CE91F525268D7AD71F}

Le nœud de messages est généré automatiquement par Adobe Mobile Services et n’a généralement pas besoin d’être modifié manuellement. La description suivante est fournie à des fins de dépannage :

* &quot;messageId&quot;
* ID généré, obligatoire
* &quot;template&quot;
   * &quot;alert&quot;, &quot;fullscreen&quot;, ou &quot;local&quot;
   * obligatoire

* &quot;showOffline&quot;
   * true ou false
   * false par défaut

* &quot;showRule&quot;
   * &quot;always&quot;, &quot;once&quot;, ou &quot;untilClick&quot;
   * obligatoire

* &quot;endDate&quot;
   * nombre de secondes depuis le 1er janvier 1970
   * La valeur par défaut est 2524730400.

* &quot;startDate&quot;
   * nombre de secondes depuis le 1er janvier 1970
   * La valeur par défaut est 0.

* &quot;payload&quot;
   * &quot;html&quot;
      * modèle plein écran uniquement, obligatoire
      * définition du message par html
   * &quot;image&quot;
      * plein écran uniquement, facultatif
      * URL de l’image à utiliser pour une image plein écran
   * &quot;altImage&quot;
      * plein écran uniquement, facultatif
      * nom de l’image regroupée à utiliser si l’URL spécifiée dans
         * image
         * n’est pas accessible
   * &quot;title&quot;
      * plein écran et alerte, obligatoire
      * texte de titre d’un message d’alerte ou plein écran
   * &quot;content&quot;
      * alerte et notification locale, obligatoire
      * sous-texte d’un message d’alerte ou texte de notification d’un message de notification local
   * &quot;confirm&quot;
      * alerte, facultatif
      * texte utilisé dans le bouton de confirmation
   * &quot;cancel&quot;
      * alerte, obligatoire
      * texte utilisé dans le bouton d’annulation
   * &quot;url&quot;
      * alerte, facultatif
      * action d’URL à charger en cas de clic sur le bouton de confirmation
   * &quot;wait&quot;
      * notification locale, obligatoire
      * durée d’attente (en secondes) avant de publier la notification locale après la correspondance avec ses critères



* &quot;audiences&quot;
   * ensemble d’objets qui définit comment le message doit être affiché
   * &quot;key&quot;
      * nom de variable à rechercher dans l’accès, obligatoire
* &quot;matches&quot;
   * type de correspondance utilisé lors de la comparaison
   * eq = est égal à
   * ne = n’est pas égal à
   * co = contient
   * nc = ne contient pas
   * sw = commence par
   * ew = finit par
   * ex = existe
   * nx = n’existe pas
   * lt = inférieur à
   * le = inférieur ou égal à
   * gt = supérieur à
   * ge = supérieur ou égal à
* &quot;values&quot;
   * tableau de valeurs utilisées pour correspondre à la valeur de la variable nommée dans
      * key
      * avec le type de correspondance dans
      * matches
* &quot;triggers&quot;
   * identique aux audiences, mais il s’agit de l’action au lieu de l’audience
   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;

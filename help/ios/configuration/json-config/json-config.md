---
description: Ces informations vous aideront à utiliser le fichier de configuration ADBMobile.json.
seo-description: Ces informations vous aideront à utiliser le fichier de configuration ADBMobile.json.
seo-title: Fichier de configuration JSON ADBMobile
solution: Marketing Cloud,Analytics
title: Fichier de configuration JSON ADBMobile
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: tm+mt
source-git-commit: bb7fc1c1fc6e88549a1673baedae19f808d222f0

---


# Fichier de configuration JSON ADBMobile{#adbmobile-json-config}

Ces informations vous aideront à utiliser le fichier de configuration `ADBMobile.json`.

## Référence du fichier de configuration ADBMobileConfig.json {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Vous pouvez utiliser le même fichier de configuration pour votre application sur différentes plateformes :

>[!TIP]
>
>Sous **iOS**, vous pouvez placer le fichier `ADBMobileConfig.json` à n’importe quel endroit accessible de votre lot.

* **acquisition**

   Permet l’acquisition des applications mobiles.

   Si cette section manque, activez l’acquisition de l’application mobile et téléchargez à nouveau le fichier de configuration du SDK. Pour plus d’informations, voir *referrerTimeout* ci-dessous.

   * `server` : serveur d’acquisition vérifié au lancement initial et devant contenir un référent d’acquisition.
   * `appid` : identifiant généré qui permet d’identifier de manière unique cette application sur le serveur d’acquisition.
   * Version minimale du SDK : 4.1

* **analyticsForwardingEnabled**

   Propriété dans l’objet `audienceManager`. Si `Audience Manager` est configuré et que `analyticsForwardingEnabled` est défini sur `true`, tout le trafic Analytics est également transféré à Audience Manager. La valeur par défaut est `false`.

   * Version minimale du SDK : 4.8.0

* **backdateSessionInfo**

   Active/désactive la capacité pour le SDK Adobe d’antidater les accès aux informations de session.

   Actuellement, les accès aux informations de session comprennent les blocages et les durées de session. Ils peuvent être activés ou désactivés.

   * Si vous définissez la valeur sur `false`, les accès sont **désactivés**.

      Le SDK revient à son comportement pré-4.1, c’est-à-dire qu’il regroupe les informations de la session précédente avec le premier accès de la session suivante. Le SDK Adobe joint également les informations de session au cycle de vie actuel, ce qui évite la création d’une visite gonflée. Puisque plus aucune visite gonflée n’est créée, on constate une baisse immédiate du nombre de visites.

   * Si vous ne spécifiez aucune valeur, la valeur par défaut est `true` et les accès sont **activés**.

      Lorsque les accès sont activés, le SDK Adobe antidate l’accès aux informations de session d’une seconde après le dernier accès à la session précédente. Ceci signifie que les données de blocage et de session sont corrélées avec la date correcte à laquelle ces événements se sont produits. Néanmoins, un inconvénient peut se produire : le SDK peut créer une visite pour l’accès antidaté. Une correspondance subit un effet rétroactif à chaque nouveau lancement de l’application.

   * Version minimale du SDK : 4.6
   >[!IMPORTANT]
   >
   >Les informations d’accès aux sessions antidatées sont envoyées dans un appel de serveur d’informations de session et des appels de serveur supplémentaires peuvent être requis.


* **batchLimit**

   Nombre limite d’accès pouvant faire l’objet d’appels consécutifs. Si, par exemple, `batchLimit` est défini sur 10, chaque accès précédant le 10e accès est placé en file d’attente. Lorsque le 10e accès intervient, les 10 accès sont tous envoyés consécutivement.

   * La valeur par défaut est `0`, ce qui signifie que le traitement par lot n’est pas activé.
   * Nécessite `offlineEnabled = true`.
   * Version minimale du SDK : 4.1

* **charset**

   Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports. Pour en savoir plus, voir [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

   * Version minimale du SDK : 4.0

* **clientCode**

   Code client qui vous a été attribué.

   >[!IMPORTANT]
   >
   >Cette variable est requise par Target.

   * Version minimale du SDK : 4.0

* **coopUnsafe**

   Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste noire sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

   À noter :

   * Si `coopUnsafe` est défini sur `coop_unsafe=1``true`, sera toujours annexé aux accès Audience Manager et identifiants visiteur.
   * Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.
   Voici quelques informations supplémentaires :

   * Version minimale du SDK : 4.16.1
   * Propriété booléenne de l’objet `marketingCloud` qui, lorsqu’elle est définie sur `true`, entraîne l’exclusion du périphérique de la solution Device Co-op d’Experience Cloud.
   * La valeur par défaut est `false`.
   * Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.



* **environmentId**

   Identifiant de l’environnement que vous souhaitez utiliser. Vous pouvez spécifier un identifiant valide (`environmentId=8`) et, si `environmentId` n’est pas inclus, l’environnement de production par défaut est utilisé.

   * Version minimale du SDK : 4.14

* **lifecycleTimeout**

   La valeur par défaut est de 300 secondes.

   Spécifie la durée, en secondes, qui doit s’écouler entre les lancements de l’application pour qu’un lancement soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque l’application est placée en arrière-plan et réactivée. La durée passée en arrière-plan n’est pas prise en compte dans la durée de la session.

   * Version minimale du SDK : 4.0

* **messages**

   Générée automatiquement par Adobe Mobile Services. Définit les paramètres pour la messagerie in-app. Pour obtenir plus d’informations, voir la section *Description des messages* ci-dessous.

   * Version minimale du SDK : 4.2

* **offlineEnabled**

   Lorsque cette variable est activée, les accès sont placés en file d’attente pendant que l’appareil est hors ligne et envoyés ultérieurement quand l’appareil est en ligne. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne. La valeur par défaut est `false`.

   Voici quelques informations importantes :

   * Si les horodatages sont activés sur votre suite de rapports, votre propriété de configuration `offlineEnabled` *doit* être définie sur « true ».
   * Si la suite de rapports n’est pas horodatée, la propriété de configuration `offlineEnabled` *doit* être définie sur « false ».

      En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée, contactez l’assistance clientèle ou téléchargez le fichier de configuration depuis Adobe Mobile Services. Si vous collectez actuellement des données AppMeasurement dans une suite de rapports qui collecte également des données de JavaScript, il est possible que vous deviez configurer une suite de rapports distincte pour les données mobiles ou que vous deviez inclure un horodatage personnalisé pour tous les accès JavaScript à l’aide de la variable `s.timestamp`.

   * Version minimale du SDK : 4.0

* **org**

   Indique l’ID d’organisation Experience Cloud pour le service d’identification Adobe Experience Platform.

   * Version minimale du SDK : 4.3

* **poi**

   Chaque matrice de points ciblés comporte le nom, la latitude, la longitude et le rayon (en mètres) du point ciblé correspondant à la zone du point. Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé et que les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelle est renseignée et envoyée avec l’appel `trackLocation`.

   * Version minimale du SDK : 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >À partir de la version 4.2, les points ciblés sont définis dans l’interface Adobe Mobile et synchronisés dynamiquement avec les fichiers de configuration de l’application. Cette synchronisation requiert le paramètre `analytics.poi` :

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Si ce paramètre n’est pas configuré, le fichier `ADBMobile.json` doit être mis à jour afin d’inclure cette ligne. Pour télécharger un fichier de configuration mis à jour, voir [Avant de démarrer](/help/ios/getting-started/requirements.md).

* **postback**

   La définition du modèle de message « callback » est présentée ci-dessous :

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   L’objet `payload` présent dans le code est un exemple de charge utile pour la définition d’un message qui irait dans la fichier `ADBMobileConfig.json`. Pour en savoir plus, consultez la rubrique [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Version minimale du SDK : 4.6

* **privacyDefault**

   * Pour `optedin`, les accès sont envoyés immédiatement.
   * Pour `optedout`, les accès sont ignorés.
   * Pour `optunknown`, si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne « inclusion » (les accès sont envoyés) ou « exclusion » (les accès sont ignorés).

      Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      Cela ne définit que la valeur initiale. Si cette valeur est définie ou modifiée dans le code, la nouvelle valeur est utilisée jusqu’à ce qu’elle soit à nouveau modifiée, ou lorsque l’application est désinstallée et réinstallée. La valeur par défaut est `optedin`.

   * Version minimale du SDK : 4.0

* **referrerTimeout**

   Durée (en secondes) pendant laquelle le SDK attend les données du référent d’acquisition lors du lancement initial avant l’expiration de la session. Si vous utilisez Acquisition, un délai de 5 secondes est recommandé.

   >[!IMPORTANT]
   >
   >Cette variable est requise par Acquisition. Si la variable est définie sur `0` ou n’est pas incluse, le SDK n’attend pas les données d’acquisition et le suivi des mesures d’acquisition n’est pas effectué.

   * Version minimale du SDK : 4.1

* **remotes**

   Configurée automatiquement et définit les points de terminaison hébergés par Adobe pour les fichiers de configuration dynamiques. L’heure de la dernière mise à jour de chaque fichier de configuration est comparée à la version en cours à chaque lancement ; les mises à jour sont téléchargées et enregistrées.

   * `analytics.poi` est le point de terminaison de la configuration des points ciblés hébergés.

   * `messages` est le point de terminaison de la configuration des messages in-app hébergés.

   * Version minimale du SDK : 4.2

* **rsids**

   Une ou plusieurs suites de rapports où seront envoyées les données Analytics. Plusieurs identifiants de suite de rapports doivent être séparés par une virgule, sans espace.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Cette variable est requise par Analytics.

   * Version minimale du SDK : 4.0

* **server**

   Serveur Analytics ou de la gestion de l’audience, en fonction du nœud parent.

   Cette variable doit être renseignée par le domaine du serveur, sans préfixe de protocole `https://` ou `https://`. Ce préfixe est géré automatiquement par la bibliothèque en fonction de la variable `ssl`.

   Si `ssl` est défini sur `true`, une connexion sécurisée est établie avec le serveur. Si `ssl` est défini sur `false`, une connexion non sécurisée est établie avec le serveur.

   >[!IMPORTANT]
   >
   >Cette variable est requise par Analytics et/ou la gestion de l’audience.

   * Version minimale du SDK : 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > Depuis la version 4.10.0, SSL prend la valeur true par défaut si l’indicateur n’est pas défini.

   Active (`true`) ou désactive (`false`) la fonctionnalité d’envoi des données de mesure en utilisant SSL (HTTPS).

   La définition du modèle de message « callback » est présentée ci-dessous :

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   L’objet `payload` du code est un exemple de charge utile pour une définition de message qui va dans le fichier `ADBMobileConfig.json`. Pour en savoir plus, consultez la rubrique [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Version minimale du SDK : 4.0

* **timeout**

   Détermine le délai pendant lequel Target attend une réponse.

   * Version minimale du SDK : 4.0


## Exemple de fichier `ADBMobileConfig.json` :{#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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

Le nœud des messages est généré automatiquement par Adobe Mobile Services et, en général, ne requiert pas de modification manuelle. La description suivante est fournie à des fins de dépannage :

* "messageId"

   * ID généré, requis

* "template"

   * "alert", "fullscreen" ou "local"
   * requis

* "payload"

   * "html"

      * modèle Plein écran uniquement, requis
      * html définissant le message
   * "image"

      * plein écran uniquement, facultatif
      * URL vers l’image à utiliser pour une image Plein écran
   * "altImage"

      * plein écran uniquement, facultatif
      * nom de l’image en lot à utiliser si l’URL spécifiée dans
         `image` n’est pas accessible
   * "title"

      * plein écran et alerte, requis
      * texte du titre pour un message Plein écran ou d’alerte
   * "content"

      * alerte et notification locale, requis
      * sous-texte pour un message d’alerte ou texte de notification pour un message de notification locale
   * "confirm"

      * alerte, facultatif
      * texte du bouton de confirmation
   * "cancel"

      * alerte, requis
      * texte du bouton d’annulation
   * "url"

      * alerte, facultatif
      * action d’url à charger si un clic a été effectué sur le bouton de confirmation
   * "wait"

      * notification locale, requis
      * durée d’attente (en secondes) avant la publication de la notification locale après la correspondance de ses critères









* "showOffline"

   * true ou false
   * la valeur par défaut est false

* "showRule"

   * "always", "once" ou "untilClick"
   * requis

* "endDate"

   * nombre de secondes depuis le 1er janvier 1970
   * La valeur par défaut est 2524730400.

* "startDate"

   * nombre de secondes depuis le 1er janvier 1970
   * La valeur par défaut est 0.

* "audiences"

   Ensemble d’objets qui définit comment le message doit être affiché :

   * "key"

      Nom de variable à rechercher dans l’accès (requis).

   * "matches"

      Type de correspondance utilisé lors de la comparaison :

      * eq = est égal à
      * ne = n’est pas égal
      * co = contient
      * nc = ne contient pas
      * sw = commence par
      * ew = se termine par
      * ex = existe
      * nx = n’existe pas
      * lt = inférieur à
      * le = inférieur à ou est égal à
      * gt = supérieur à
      * ge = supérieur à ou est égal à
   * « values »

      Tableau de valeurs utilisées pour correspondre à la valeur de la variable nommée dans ce qui suit :

      * key
      * avec le type de comparateur dans
      * matches


* « triggers »

   Comme les audiences, mais il s’agit ici des actions :

   * « key »
   * « matches »
   * « values »

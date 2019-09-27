---
description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-title: Configuration ADBMobileConfig.json
solution: Marketing Cloud,Analytics
title: Configuration ADBMobileConfig.json
topic: Développeur et mise en œuvre
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac98545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Fichier de configuration ADBMobileConfig.json {#adbmobileconfig-json-config}

Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes de configuration est « Config ».

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. Plusieurs identifiants de suite de rapports doivent être séparés par une virgule, sans espace.

   * Voici la syntaxe de cette méthode :

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Requis par Analytics et Gestion de l’audience**). Serveur d’Analytics ou de la gestion de l’audience, en fonction du nœud parent. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la variable `ssl`.

   Si `ssl` est défini sur `true`, une connexion sécurisée est établie avec le serveur. Si `ssl` est défini sur `false`, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). La valeur par défaut est `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si l’horodatage d’une suite de rapports est activé, contactez le service à la clientèle. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   La valeur par défaut est `false`.

* **lifecycleTimeout**

   Spécifie la durée, en secondes, qui doit s’écouler entre les lancements de l’application pour qu’un lancement soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque l’application est placée en arrière-plan et réactivée. La durée passée en arrière-plan n’est pas prise en compte dans la durée de la session.

   La valeur par défaut est de 300 secondes.

* **batchLimit**

   Envoie les accès par lots.

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Nécessite `offlineEnabled=true`et la valeur par défaut est `0` (Pas de traitement par lot).

* **privacyDefault**

   Les options sont les suivantes :

   * `optedin` - les accès sont envoyés immédiatement.
   * `optedout` - les accès sont ignorés.
   * `optunknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      This sets the default value only. Si cette valeur est définie ou modifiée dans le code, la valeur définie par le code est enregistrée dans le stockage local et utilisée jusqu’à ce qu’elle soit modifiée ou que l’application soit désinstallée, puis réinstallée.

      La valeur par défaut est `optedin`.

* **poi**

   Chaque matrice de points ciblés comporte le nom, la latitude, la longitude et le rayon (en mètres) du point ciblé correspondant à la zone du point. Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé, si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici l’exemple de code de cette variable :

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Détermine le délai pendant lequel Target attend une réponse.

Voici un exemple de fichier `ADBMobileConfig.json` :

```js
{ 
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```

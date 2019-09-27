---
description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-title: Fichier de configuration ADBMobileConfig.json
solution: Marketing Cloud,Analytics
title: Fichier de configuration ADBMobileConfig.json
topic: Développeur et mise en œuvre
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` fichier de configuration {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes de configuration est « Config ».

* **rsids**

   (Requis par Analytics) Une ou plusieurs suites de rapports permettant de recevoir des données Analytics. Plusieurs identifiants de suite de rapports doivent être séparés par une virgule, sans espace.

   * Voici des exemples de code pour cette variable :

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Requis par Analytics et Gestion de l’audience). Serveur d’Analytics ou de la gestion de l’audience, en fonction du nœud parent. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la variable `ssl`.

   Si `ssl` est défini sur `true`, une connexion sécurisée est établie avec le serveur. Si `ssl` est défini sur `false`, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). La valeur par défaut est `false`.

* **offlineEnabled**

   Lorsque cette propriété est activée (true/false), les accès sont placés en file d’attente quand l’appareil est hors ligne et envoyés ultérieurement une fois l’appareil en ligne. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Sinon, la propriété de configuration `offlineEnabled` *doit* être définie sur « false ». En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée, contactez Assistance clientèle. Si vous collectez actuellement des données AppMeasurement dans une suite de rapports qui collecte également des données depuis JavaScript, il est possible que vous deviez configurer une suite de rapports distincte pour les données mobiles ou que vous deviez inclure un horodatage personnalisé pour tous les accès JavaScript à l’aide de la variable `s.timestamp`.

* **lifecycleTimeout**

   Spécifie la durée, en secondes, qui doit s’écouler entre les lancements de l’application pour qu’un lancement soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque l’application est placée en arrière-plan et réactivée. La durée passée en arrière-plan n’est pas prise en compte dans la durée de la session. La valeur par défaut est de 300 secondes.

* **batchLimit**

   Envoie les accès par lots. Par exemple, si la variable est définie sur 50, les accès sont mis en file d’attente jusqu’à ce que 50 soient stockés, puis tous les accès mis en file d’attente sont envoyés. Nécessite `offlineEnabled=true`. La valeur par défaut est `0` (Pas de traitement par lot).

* **privacyDefault**

   * `optedin` - les accès sont envoyés immédiatement.
   * `optedout` - les accès sont ignorés.
   * `optunknown` : si l’horodatage est activé pour la suite de rapports, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in ; alors les accès sont envoyés) ou sur exclusion (opt-out ; les accès sont ignorés). Sinon, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (opt-in).

      La valeur par défaut est `optedin`.

      >[!TIP]
      >
      >Cette option définit uniquement la valeur par défaut. Si cette valeur est définie ou modifiée dans le code, la valeur définie par le code est enregistrée dans le stockage local et utilisée jusqu’à ce qu’elle soit modifiée ou que l’application soit désinstallée, puis réinstallée.

* **poi**

   Chaque matrice de points ciblés comporte le nom, la latitude, la longitude et le rayon (en mètres) du point ciblé correspondant à la zone du point. Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé, si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici l’exemple de code de cette variable :

      ```js
      "poi": [
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


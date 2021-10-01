---
description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
solution: Experience Cloud,Analytics
title: Configuration de ADBMobileConfig.json
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 42%

---

# Fichier de configuration ADBMobileConfig.json {#adbmobileconfig-json-config}

Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Les méthodes de configuration comportent le préfixe &quot;Config&quot;.

* **rsids**

   (**Requis par Analytics**) Une ou plusieurs suites de rapports pour recevoir des données Analytics. Plusieurs ID de suite de rapports doivent être séparés par des virgules sans espace entre eux.

   * Voici la syntaxe de cette méthode :

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Requis par Analytics et gestion de l’audience**). Serveur Analytics ou de gestion de l’audience, en fonction du noeud parent. Cette variable doit être renseignée par le domaine du serveur, sans préfixe de protocole `"https://"` ou `"https://"`. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la variable `ssl` .

   Si `ssl` est`true` défini sur, une connexion sécurisée est établie avec le serveur. Si `ssl` est `false`défini sur, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères que vous utilisez pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports. Pour plus d’informations, voir la variable [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=fr) dans la documentation Adobe Analytics.

* **ssl**

   Active (`true`) ou désactive (`false`) l’envoi de données de mesure via SSL (`HTTPS`). La valeur par défaut est `false`.

* **offlineEnabled**

   Lorsque cette option est activée (`true`), les accès sont placés en file d’attente lorsque l’appareil est hors ligne et envoyés ultérieurement lorsque l’appareil est en ligne. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   Si les horodatages sont activés sur votre suite de rapports, la `offlineEnabled` propriété de configuration *doit* être `true`. si l’horodatage de votre suite de rapports n’est pas activé, la `offlineEnabled` propriété de configuration *doit* être `false`.

   En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée, contactez l’assistance clientèle. Si vous collectez actuellement des données AppMeasurement dans une suite de rapports qui collecte également des données de JavaScript, vous devrez peut-être configurer une suite de rapports distincte pour les données mobiles ou inclure un horodatage personnalisé pour tous les accès JavaScript à l’aide de la variable `s.timestamp` .

   La valeur par défaut est `false`.

* **lifecycleTimeout**

   Spécifie la durée, en secondes, qui doit s’écouler entre le lancement de l’application et le moment où le lancement est considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque votre application est envoyée en arrière-plan et réactivée. Le temps passé par votre application en arrière-plan n’est pas inclus dans la durée de session.

   La valeur par défaut est de 300 secondes.

* **batchLimit**

   Envoyez les accès par lots.

   Par exemple, si la valeur est `50`, les accès sont placés en file d’attente jusqu’à ce que 50 soient stockés, puis tous les accès en file d’attente sont envoyés. Nécessite `offlineEnabled=true` et la valeur par défaut est `0` (Pas de traitement par lot).

* **privacyDefault**

   Les options sont les suivantes :

   * `optedin` - les accès sont immédiatement envoyés.
   * `optedout` - les accès sont ignorés.
   * `optunknown` - Si la suite de rapports prend en charge l’horodatage, les accès sont enregistrés jusqu’à ce que l’état de confidentialité devienne &quot;inclusion&quot; (les accès sont envoyés) ou &quot;exclusion&quot; (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      Cette option définit uniquement la valeur par défaut. Si cette valeur est jamais définie ou modifiée dans le code, alors la valeur définie par le code est enregistrée dans le stockage local et est utilisée à l’avenir jusqu’à ce qu’elle soit modifiée, ou jusqu’à ce que l’application soit désinstallée puis réinstallée.

      La valeur par défaut est `optedin`.

* **poi**

   Chaque matrice de points ciblés comporte le nom, la latitude, la longitude et le rayon (en mètres) du point ciblé correspondant à la zone du point. Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé, si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici l’exemple de code pour cette variable :

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Requis par Target**) Votre code client affecté.

* **timeout**

   Détermine le délai pendant lequel la cible attend une réponse.

Voici un exemple de fichier `ADBMobileConfig.json` :

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

---
description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-description: Informations relatives à l’utilisation du fichier de configuration JSON ADBMobile.
seo-title: Fichier de configuration ADBMobileConfig.json
solution: Experience Cloud,Analytics
title: Fichier de configuration ADBMobileConfig.json
topic: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 47%

---


# `ADBMobileConfig.json` fichier de configuration {#adbmobileconfig-json-config}

Informations destinées à vous aider à utiliser le fichier de `ADBMobile.json` configuration.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Cible et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Les méthodes de configuration comportent le préfixe &quot;Config&quot;.

* **rsids**

   (Requis par Analytics) Une ou plusieurs suites de rapports pour recevoir les données Analytics. Plusieurs ID de suite de rapports doivent être séparés par des virgules sans espace entre eux.

   * Voici des exemples de code pour cette variable :

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Requis par Analytics et la gestion des Audiences). Analytics ou serveur de gestion des Audiences, en fonction du noeud parent. Cette variable doit être renseignée par le domaine du serveur, sans préfixe de protocole `https://` ou `https://`. Le préfixe de protocole est géré automatiquement par la bibliothèque en fonction de la `ssl` variable.

   Si `ssl` est`true` défini sur, une connexion sécurisée est établie avec le serveur. Si `ssl` est `false`défini sur, une connexion non sécurisée est établie avec le serveur.

* **charset**

   Définit le jeu de caractères utilisé pour les données envoyées à Analytics. La variable charset est utilisée pour convertir des données entrantes au format UTF-8 pour stockage et création de rapports. Pour en savoir plus, voir [s.charSet](https://docs.adobe.com/content/help/fr-FR/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Active (`true`) ou désactive (`false`) l&#39;envoi de données de mesure via SSL (HTTPS). La valeur par défaut est `false`.

* **offlineEnabled**

   Lorsque cette option est activée (true), les accès sont placés en file d’attente lorsque le périphérique est hors ligne et envoyés ultérieurement lorsque le périphérique est en ligne. La suite de rapports doit prendre en charge l’horodatage pour permettre l’utilisation du suivi hors ligne.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Si la suite de rapports n’est pas horodatée, la propriété de configuration `offlineEnabled` *doit* être définie sur « false ». En cas de configuration incorrecte, les données seront perdues. Si vous ne savez pas si une suite de rapports est horodatée,   contactez   Assistance clientèle. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

* **lifecycleTimeout**

   Spécifie la durée, en secondes, qui doit s’écouler entre le lancement de l’application et le moment où le lancement est considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque votre application est envoyée en arrière-plan et réactivée. Le temps passé par votre application en arrière-plan n’est pas inclus dans la durée de session. La valeur par défaut est de 300 secondes.

* **batchLimit**

   Envoyer les accès par lots. Par exemple, si la valeur est définie sur 50, les accès sont placés en file d’attente jusqu’à ce que 50 soient stockés, puis tous les accès en file d’attente sont envoyés. Nécessite `offlineEnabled=true`. La valeur par défaut est `0` (Pas de traitement par lot).

* **privacyDefault**

   * `optedin` - les accès sont immédiatement envoyés.
   * `optedout` - les accès sont ignorés.
   * `optunknown` - Si votre suite de rapports est horodatée, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont alors envoyés) ou sur exclusion (les accès sont ignorés). Si la suite de rapports ne prend pas en charge l’horodatage, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur « inclusion ».

      La valeur par défaut est `optedin`.

      >[!TIP]
      >
      >Cette option définit uniquement la valeur par défaut. Si cette valeur est définie ou modifiée dans le code, la valeur définie par le code est enregistrée dans l’enregistrement local et est utilisée à partir de maintenant jusqu’à ce qu’elle soit modifiée, ou que l’application soit désinstallée puis réinstallée.

* **poi**

   Chaque matrice de points ciblés comporte le nom, la latitude, la longitude et le rayon (en mètres) du point ciblé correspondant à la zone du point. Le nom du point ciblé peut être n’importe quelle chaîne. Lorsqu’un appel `trackLocation` est envoyé, si les coordonnées actuelles se trouvent dans un point ciblé défini, une variable de données contextuelles est renseignée et envoyée avec l’appel `trackLocation`.

   * Voici un exemple de code pour cette variable :

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Obligatoire par Cible**) Code client affecté.

* **timeout**

   Détermine le délai pendant lequel Target attend une réponse.

The following is an example of an `ADBMobileConfig.json` file:

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


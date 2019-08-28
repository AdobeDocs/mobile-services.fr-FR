---
description: Ces informations vous aideront à migrer de la version 2.x ou 3.x de la bibliothèque iOS vers la version 4.x.
seo-description: Ces informations vous aideront à migrer de la version 2.x ou 3.x de la bibliothèque iOS vers la version 4.x.
seo-title: Migration vers la bibliothèque ios 4. x
solution: Marketing Cloud, Analytics
title: Migration vers la bibliothèque ios 4. x
topic: Développeur et mise en œuvre
uuid: 5668972 b-f 355-4 e 03-9 df 0-8 c 82 ddf 6809 b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

Ces informations vous aideront à migrer de la version 2.x ou 3.x de la bibliothèque iOS vers la version 4.x.

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Si vous modifiez ou supprimez dans `NSUserDefaults` des valeurs attendues par le SDK, il peut en résulter un comportement inattendu sous la forme de données incohérentes.

Dans la version 4. x de la bibliothèque SDK ios, les méthodes publiques sont consolidées dans un seul en-tête. De plus, la fonctionnalité est maintenant accessible par le biais des méthodes de niveau classe, de sorte que vous n'ayez pas à effectuer le suivi des pointeurs, des instances ou des singletons.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Dans la version 4, vous ne pouvez plus attribuer des variables telles que des événements, des eVars, des props, des héritiers et des listes directement dans votre application. À la place, le SDK utilise des données contextuelles et des règles de traitement pour mapper vos données d’application aux variables Analytics pour la création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mises en correspondance à l’aide des règles de traitement.

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Le nouveau fichier `ADBMobileConfig.json` comporte des paramètres globaux, spécifiques à une application et remplace la plupart des variables de configuration utilisées dans les versions précédentes. Voici un exemple de fichier `ADBMobileConfig.json` :

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
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```


### Déplacement du fichier de configuration

Pour déplacer le fichier de configuration, procédez comme suit :

1. Déplacez la valeur qui est définie pour la variable dans la première colonne vers la variable dans la deuxième colonne.
1. Supprimez l’ancienne variable de configuration du code.

### Informations de migration

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration.

#### Migration depuis la version 3.x

Déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| offlineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Supprimée, n’est plus utilisée. |
| linkTrackEvents | Supprimée, n’est plus utilisée. |


#### Migration depuis la version 2.x

Déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", supprimez le `"https://"` préfixe. Le préfixe du protocole est ajouté automatiquement en fonction du paramètre "ssl". |
| trackingServerSecure | Supprimée. Pour les connexions sécurisées, définissez "server", puis activez "ssl". |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Supprimée, n’est plus utilisée. |
| linkTrackEvents | Supprimée, n’est plus utilisée. |
| timestamp | Supprimée, ne peut plus être configurée. |
| dc | Supprimée, n’est plus utilisée. |
| userAgent | Supprimée, ne peut plus être configurée. |
| dynamicVariablePrefix | Supprimée, n’est plus utilisée. |
| visitorNamespace | Supprimée, n’est plus utilisée. |
| usePlugins | Supprimée, n’est plus utilisée. |
| useBestPractices  tous les appels à la mesure churn (getChurnInstance ) | Supprimer, remplacé par des mesures de cycle de vie. Pour en savoir plus, voir la section [Mesures de cycle de vie](//help/ios/metrics.md). |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les appels web `track` et `trackLink`, le SDK version 4 utilise les méthodes suivantes :

* `trackState:data:` sont les vues disponibles dans votre application, telles `home dashboard`que `app settings``cart`, etc.

   Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* `trackAction:data:` actions, telles `logons`que, `banner taps``feed subscriptions`et d'autres mesures qui se produisent dans votre application et que vous souhaitez mesurer.

Le paramètre `data` pour ces deux méthodes est un `NSDictionary` qui contient des paires nom-valeur envoyées en tant que données contextuelles.

### Evénements, props, evars

Dans la version 4, vous ne pouvez plus affecter des variables telles que les événements, les eVars, les props, les héritiers et les listes directement dans votre application. Le SDK utilise désormais les données contextuelles et les règles de traitement pour faire correspondre les données de l’application aux variables Analytics pour la création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mappées à l’aide des règles de traitement. Pour plus d'informations, voir [Règles de traitement et données contextuelles](/help/ios/getting-started/proc-rules.md).

Les valeurs que vous avez directement attribuées aux variables doivent être ajoutées au   `data``NSDictionary` à la place. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### Appsection/Server, geozip, ID de transaction, Campagne et autres variables standard

Les données que vous configuriez sur l’objet de mesure, y compris les variables répertoriées ci-dessus, doivent être ajoutées au   `data``NSDictionary` à la place. Les seules données envoyées avec un appel `trackState` ou `trackAction` sont la charge utile dans le paramètre `data`.

### Remplacement des appels de suivi

Dans le code, remplacez les méthodes suivantes par un appel à `trackState` ou `trackAction` :

#### Migration depuis la version 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migration depuis la version 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier:`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Dans le code, supprimez les appels aux méthodes suivantes :

### Version 3.x

* `setOnline`
* `setOffline`

### Version 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Puisque la variable `products` n’est plus disponible dans les règles de traitement, vous pouvez utiliser la syntaxe suivante pour la définir :

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)
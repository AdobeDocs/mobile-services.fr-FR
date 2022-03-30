---
description: Ces informations vous aideront à migrer de la version 2.x ou 3.x de la bibliothèque iOS vers la version 4.x.
solution: Experience Cloud Services,Analytics
title: Migration vers la bibliothèque iOS 4.x
topic-fix: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
exl-id: a58067e0-b6f4-4900-ba3f-7256d9259420
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 100%

---

# Migration vers la bibliothèque iOS 4.x{#migrating-to-the-x-ios-library}

Ces informations vous aideront à migrer de la version 2.x ou 3.x de la bibliothèque iOS vers la version 4.x.

>[!IMPORTANT]
>
>Le SDK utilise `NSUserDefaults` pour stocker les données nécessaires au calcul d’utilisateurs uniques, de mesures de cycle de vie et d’autres données nécessaires dans le cadre du fonctionnement de base du SDK.  Si vous modifiez ou supprimez dans `NSUserDefaults` des valeurs attendues par le SDK, il peut en résulter un comportement inattendu sous la forme de données incohérentes.

Dans la bibliothèque du SDK iOS version 4.x, les méthodes publiques sont consolidées dans un en-tête. En outre, les fonctionnalités sont désormais accessibles par des méthodes de niveau de classe : ainsi, il n’est pas nécessaire d’effectuer le suivi des pointeurs, des instances ou des singletons.

## Événements, props et eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Dans la version 4, vous ne pouvez plus affecter de variables telles que des événements, des eVars, des props, des héritiers et des listes directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application sur les variables Analytics à des fins de reporting.

Les règles de traitement offrent les avantages suivants :

* Vous pouvez modifier le mapping de vos données sans envoyer de mise à jour à la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact.

   Ces valeurs n’apparaîtront dans les rapports qu’après avoir été mappées à l’aide de règles de traitement.

>[!TIP]
>
>Les valeurs que vous assignez directement aux variables doivent désormais être ajoutées au NSDictionary `data`.

## Suppression des propriétés non utilisées {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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

Pour déplacer le fichier de configuration :

1. Déplacez la valeur définie pour la variable dans la première colonne vers la variable dans la seconde colonne.
1. Supprimez l’ancienne variable de configuration de votre code.

### Informations de migration

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration.

#### Migration depuis la version 3.x

Déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable du fichier `ADBMobileConfig.json` |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | À supprimer, n’est plus utilisée |
| linkTrackEvents | À supprimer, n’est plus utilisée |


#### Migration depuis la version 2.x

Déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable du fichier `ADBMobileConfig.json` |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, supprimez le préfixe `"https://"`. Le préfixe de protocole est ajouté automatiquement en fonction du paramètre &quot;ssl&quot;. |
| trackingServerSecure | À supprimer. Pour les connexions sécurisées, définissez &quot;server&quot;, puis activez &quot;ssl&quot;. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | À supprimer, n’est plus utilisée |
| linkTrackEvents | À supprimer, n’est plus utilisée |
| timestamp | À supprimer, ne peut plus être configurée. |
| dc | À supprimer, n’est plus utilisée |
| userAgent | À supprimer, ne peut plus être configurée. |
| dynamicVariablePrefix | À supprimer, n’est plus utilisée |
| visitorNamespace | À supprimer, n’est plus utilisée |
| usePlugins | À supprimer, n’est plus utilisée |
| useBestPractices  tous les appels à la mesure churn (getChurnInstance) | Supprimée, remplacée par des mesures de cycle de vie. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md). |


## Mise à jour des appels et des variables de suivi {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les appels web `track` et `trackLink`, le SDK version 4 utilise les méthodes suivantes :

* Les états `trackState:data:` sont les affichages disponibles dans l’application, par exemple `home dashboard`, `app settings`, `cart`, etc.

   Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* Les actions `trackAction:data:`, par exemple `logons`, `banner taps`, `feed subscriptions`, etc. qui se produisent dans l’application et que vous souhaitez mesurer.

Le paramètre `data` pour ces deux méthodes est un `NSDictionary` qui contient des paires nom-valeur envoyées en tant que données contextuelles.

### Événements, props et eVars

Dans la version 4, vous ne pouvez plus affecter de variables telles que des événements, des eVars, des props, des héritiers et des listes directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application sur les variables Analytics à des fins de reporting.

Les règles de traitement offrent les avantages suivants :

* Vous pouvez modifier le mapping de vos données sans envoyer de mise à jour à la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact.

   Ces valeurs n’apparaîtront dans les rapports qu’après avoir été mappées à l’aide de règles de traitement. Pour plus d’informations, voir [Règles de traitement et données contextuelles](/help/ios/getting-started/proc-rules.md).

Les valeurs que vous avez directement attribuées aux variables doivent être ajoutées au `data` `NSDictionary` à la place. Cela signifie que les appels vers `setProp`, `setEvar` et les attributions à des données contextuelles persistantes doivent être supprimés et les valeurs doivent être ajoutées au paramètre `data`.

### AppSection/Server, GeoZip, transaction ID, Campaign et autres variables standard

Les données que vous configuriez sur l’objet de mesure, y compris les variables répertoriées ci-dessus, doivent être ajoutées au `data` `NSDictionary` à la place. Les seules données envoyées avec un appel `trackState` ou `trackAction` sont la charge utile dans le paramètre `data`.

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

## Identifiant visiteur personnalisé {#section_2CF930C13BA64F04959846E578B608F3}

Remplacez la variable `visitorID` par un appel à `setUserIdentifier:`.

## Suivi hors ligne {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Le suivi hors ligne est activé dans le fichier `ADBMobileConfig.json` et le reste de la configuration hors ligne est effectué automatiquement.

Dans le code, supprimez les appels aux méthodes suivantes :

### Version 3.x

* `setOnline`
* `setOffline`

### Version 2.x

* `forceOffline`
* `forceOnline`

## Variable products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Puisque la variable `products` n’est plus disponible dans les règles de traitement, vous pouvez utiliser la syntaxe suivante pour la définir :

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)

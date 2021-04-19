---
description: Cette section décrit comment migrer de la version 3.x d’un SDK mobile Windows précédent vers le SDK Windows 8.1 Universal App Store 4.x pour les solutions Experience Cloud.
seo-description: Cette section décrit comment migrer de la version 3.x d’un SDK mobile Windows précédent vers le SDK Windows 8.1 Universal App Store 4.x pour les solutions Experience Cloud.
seo-title: Migration vers les SDK 4.x
solution: Experience Cloud,Analytics
title: Migration vers les SDK 4.x
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 24%

---

# Migration vers les SDK 4.x {#migrate-to-the-x-sdks}

Cette section décrit comment migrer de la version 3.x d’un SDK mobile Windows précédent vers le SDK Windows 8.1 Universal App Store 4.x pour les solutions Experience Cloud.

Avec le passage à la version 4.x, toutes les fonctionnalités sont désormais accessibles par le biais de méthodes statiques, donc plus de suivi de vos propres objets.

Les sections suivantes décrivent la migration de la version 3.x à la version 4.x.

## Suppression des propriétés non utilisées {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Vous avez probablement remarqué un nouveau fichier `ADBMobileConfig.json` inclus dans votre téléchargement. Ce fichier contient des paramètres globaux spécifiques à l’application et remplace la plupart des variables de configuration utilisées dans les versions précédentes. Voici un exemple de fichier `ADBMobileConfig.json` :

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration. Déplacez la valeur définie pour la variable dans la première colonne vers la variable dans la seconde colonne, puis supprimez l’ancienne variable de configuration de votre code.

## Migration à partir de la version 3.x

| Variable/méthode de configuration | Variable dans le fichier `ADBMobileConfig.json`. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Supprimer, n’est plus utilisé. |
| linkTrackVars | Supprimer, n’est plus utilisé. |
| linkTrackEvents | Supprimer, n’est plus utilisé. |

## Mise à jour des appels et des variables de suivi {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les appels `Track` et `TrackLink` Web, le SDK version 4 utilise deux méthodes qui ont un peu plus de sens dans le monde mobile :

* `TrackState` Les états sont les vues disponibles dans votre application, telles que &quot;tableau de bord d’accueil&quot;, &quot;paramètres de l’application&quot;, &quot;panier&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* `TrackAction` Les actions sont les actions qui se produisent dans votre application et que vous souhaitez mesurer, telles que les &quot;connexions&quot;, les &quot;clics sur la bannière&quot;, les &quot;abonnements de flux&quot; et d’autres mesures. Ces appels n’incrémentent pas les vues de page.

Le paramètre `contextData` pour ces deux méthodes contient des paires nom-valeur qui sont envoyées en tant que données contextuelles.

## Événements, props, eVars

Si vous avez examiné les méthodes [SDK](/help/windows-appstore/c-configuration/methods.md), vous vous demandez probablement où définir des événements, des eVars, des props, des héritiers et des listes. Dans la version 4, vous ne pouvez plus affecter ces types de variables directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application sur les variables Analytics à des fins de reporting.

Les règles de traitement offrent plusieurs avantages :

* Vous pouvez modifier le mapping de vos données sans envoyer de mise à jour à la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact. Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne seront pas mises en correspondance à l’aide de règles de traitement.

Pour plus d’informations, voir *Règles de traitement* dans [Analytics](/help/windows-appstore/analytics/analytics.md).

Toutes les valeurs que vous affectiez directement aux variables doivent être ajoutées aux données contextuelles. Cela signifie que les appels à `SetProp`, `SetEvar` et les affectations aux données contextuelles persistantes doivent tous être supprimés et les valeurs ajoutées aux données contextuelles.

**AppSection/Server, GeoZip, ID de transaction, Campaign et d’autres variables standard**

Toute autre donnée que vous définissez sur l’objet de mesure, y compris les variables répertoriées ci-dessus, doit être ajoutée aux données contextuelles.

Pour le dire simplement, les seules données envoyées avec un appel `TrackState` ou `TrackAction` sont la charge utile dans le paramètre `data`.

### Remplacement des appels de suivi

Dans tout votre code, remplacez les méthodes suivantes par un appel à `trackState` ou `trackAction` :

### Migration à partir de la version 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Identifiant visiteur personnalisé {#section_2CF930C13BA64F04959846E578B608F3}

Remplacez la variable `visitorID` par un appel à `setUserIdentifier`.

## Suivi hors ligne {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Le suivi hors ligne est activé dans le fichier `ADBMobileConfig.json`. Toute autre configuration hors ligne est effectuée automatiquement.

Dans tout votre code, supprimez les appels aux méthodes suivantes :

### Migration à partir de la version 3.x

* `SetOnline`
* `SetOffline`

## Variable products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Puisque la variable `products` n’est plus disponible dans les règles de traitement, vous pouvez utiliser la syntaxe suivante pour la définir :

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

Dans cet exemple, la valeur de `"&&products"` est `";Cool Shoe`&quot; et doit respecter la syntaxe de la chaîne products pour le type de événement suivi.

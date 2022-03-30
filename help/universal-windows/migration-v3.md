---
description: Cette section décrit comment migrer de la version 3.x d’un précédent SDK Windows Mobile vers le SDK Plateforme Windows universelle 4.x pour les solutions Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Migrer vers la version 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# Migration vers les SDK 4.x{#migrate-to-x}

Cette section décrit comment migrer de la version 3.x du SDK mobile Windows vers le SDK 4.x Plateforme Windows universelle pour les solutions Experience Cloud.

Avec le passage à la version 4.x, toutes les fonctionnalités sont désormais accessibles par des méthodes statiques. Vous n’avez plus besoin de suivre vos propres objets.

Les sections suivantes vous guident tout au long de la migration de la version 3.x vers la version 4.x.

## Suppression des propriétés non utilisées {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Vous avez probablement remarqué une nouvelle `ADBMobileConfig.json` inclus avec votre téléchargement. Ce fichier contient des paramètres globaux, spécifiques à l’application et remplace la plupart des variables de configuration utilisées dans les versions précédentes.

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

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration. Déplacez la valeur définie pour la variable dans la première colonne vers la variable dans la deuxième colonne, puis supprimez l’ancienne variable de configuration de votre code.

### Migration depuis la version 3.x

Le tableau suivant fournit une liste de variables dans les SDK 3.x et le nouveau nom dans les SDK 4.x :

| Variable/méthode de configuration | Variable dans la variable `ADBMobileConfig.json` fichier . |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | À supprimer, n’est plus utilisée |
| linkTrackVars | À supprimer, n’est plus utilisée |
| linkTrackEvents | À supprimer, n’est plus utilisée |

## Mise à jour des appels et des variables de suivi {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les `Track` et `TrackLink` Pour les appels, le SDK version 4 utilise deux méthodes plus logiques dans le monde mobile :

* `TrackState` Les états correspondent aux affichages disponibles dans l’application, par exemple &quot;tableau de bord d’accueil&quot;, &quot;paramètres de l’application&quot;, &quot;panier&quot;, etc. Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* `TrackAction` Les actions sont les événements qui se produisent dans l’application et que vous souhaitez mesurer, par exemple &quot;connexions&quot;, &quot;appuis sur la bannière&quot;, &quot;abonnements aux flux&quot; et d’autres mesures. Ces appels n’incrémentent pas les pages vues.

Le `contextData` pour ces deux méthodes, contient des paires nom-valeur envoyées en tant que données contextuelles.

### Événements, props et eVars

Si vous avez examiné la variable [Méthodes SDK](/help/universal-windows/c-configuration/methods.md), vous vous demandez probablement où définir les événements, eVars, props, héritiers et listes. Dans la version 4, vous ne pouvez plus affecter ces types de variables directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application sur les variables Analytics à des fins de reporting.

Les règles de traitement offrent les avantages suivants :

* Vous pouvez modifier le mapping de vos données sans envoyer de mise à jour à la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact. Ces valeurs n’apparaîtront dans les rapports qu’après avoir été mappées à l’aide de règles de traitement.

Pour plus d’informations, voir *Règles de traitement* dans [Présentation d’Analytics](/help/universal-windows/analytics/analytics.md).

Toutes les valeurs que vous assignez directement aux variables doivent être ajoutées aux données contextuelles à la place. Cela signifie que appelle à `SetProp`, `SetEvar`, les attributions à des données contextuelles persistantes doivent être supprimées et les valeurs ajoutées aux données contextuelles.

### AppSection/Server, GeoZip, transaction ID, Campaign et autres variables standard

Toutes les autres données que vous définissiez sur l’objet de mesure, y compris les variables répertoriées ci-dessus, doivent être ajoutées aux données contextuelles à la place. En d’autres termes, les seules données envoyées avec une `TrackState` ou `TrackAction` est la charge utile dans la variable `data` .

**Remplacement des appels de suivi**

Dans votre code, remplacez les méthodes suivantes par un appel à `trackState` ou `trackAction`:

**Migration depuis la version 3.x :**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Service d’ID personnalisé {#section_2CF930C13BA64F04959846E578B608F3}

Remplacez la variable `visitorID` par un appel à `setUserIdentifier`.

## Suivi hors ligne {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Le suivi hors ligne est activé dans la variable `ADBMobileConfig.json` fichier . Toute autre configuration hors ligne est effectuée automatiquement.

Dans votre code, supprimez les appels aux méthodes suivantes :

**Migration depuis la version 3.x :**

* SetOnline
* SetOffline

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

La valeur de `"&&products"` (dans cet exemple, la valeur est `";Cool Shoe`&quot;) doit suivre la syntaxe de la chaîne de produits pour le type d’événement dont vous effectuez le suivi.

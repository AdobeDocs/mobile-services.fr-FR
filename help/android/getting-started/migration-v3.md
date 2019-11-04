---
description: Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.
keywords: android;library;mobile;sdk
seo-description: Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.
seo-title: Migration vers la bibliothèque Android 4.x
solution: Experience Cloud,Analytics
title: Migration vers la bibliothèque Android 4.x
topic: Développeur et mise en œuvre
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: ht
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migration vers la bibliothèque Android 4.x {#migrating-to-the-android-x-library}

Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.

>[!IMPORTANT]
>
>Le SDK utilise `SharedPreferences` pour stocker les données nécessaires au calcul d’utilisateurs uniques, de mesures de cycle de vie et d’autres données nécessaires dans le cadre du fonctionnement de base du SDK.  Si vous modifiez ou supprimez dans `SharedPreferences` des valeurs attendues par le SDK, il peut en résulter un comportement inattendu sous la forme de données incohérentes.

Dans la bibliothèque version 4.x, les méthodes publiques sont consolidées dans un en-tête. En outre, toutes les fonctionnalités sont désormais accessibles par des méthodes de niveau de classe : ainsi, il n’est pas nécessaire d’effectuer le suivi des pointeurs, des instances ou des singletons.

## Événements, props et eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Dans la version 4, vous ne pouvez plus affecter des variables telles que les événements, les eVars, les props, les héritiers et les listes dans votre application. À la place, le SDK utilise des données contextuelles et des règles de traitement afin de faire correspondre les données de l’application aux variables Analytics à des fins de création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mises en correspondance à l’aide des règles de traitement.

>[!TIP]
>
>Les valeurs que vous avez directement attribuées aux variables doivent être ajoutées à la table de hachage HashMap `data`.

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

## Déplacement du fichier de configuration et migration vers la version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration.

### Déplacement du fichier de configuration

1. Déplacez la valeur définie pour la variable de la première colonne vers la variable de la deuxième colonne.
1. Supprimez l’ancienne variable de configuration du code.

### Migration depuis la version 3.x

Pour migrer de la version 3.x vers la version 4, déplacez la valeur de la variable/méthode de configuration vers la variable `ADBMobileConfig.json`.

| Variable ou méthode de configuration | Variable du fichier `ADBMobileConfig.json` |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Supprimée, n’est plus utilisée. |
| linkTrackEvents | Supprimée, n’est plus utilisée. |

### Migration depuis la version 2.x

Pour migrer depuis la version 2.x vers la version 4.x, déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable du fichier `ADBMobileConfig.json` |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", supprimez le préfixe `"https://"`. Le préfixe du protocole est ajouté automatiquement en fonction du paramètre "ssl". |
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
| useBestPractices  tous les appels à la mesure churn (getChurnInstance) | Supprimée, remplacée par des mesures de cycle de vie. |

## Mise à jour des appels et des variables de suivi {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les appels web `track` et `trackLink`, le SDK version 4 utilise les méthodes suivantes :

* `trackState`, qui sont les affichages disponibles dans l’application, par exemple `home dashboard`, `app settings`, `cart`, etc.

   Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* Les actions `trackAction`, par exemple `logons`, `banner taps`, `feed subscriptions` et autres, qui se produisent dans l’application et que vous souhaitez mesurer.

Le paramètre `contextData` pour ces deux méthodes est un `HashMap<String, Object>`, qui comporte les paires nom-valeur envoyées en tant que données contextuelles.

## Événements, props et eVars

Dans la version 4, vous ne pouvez plus affecter des variables telles que les événements, les eVars, les props, les héritiers et les listes directement dans votre application. Le SDK utilise désormais les données contextuelles et les règles de traitement pour faire correspondre les données de l’application aux variables Analytics pour la création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mises en correspondance à l’aide des règles de traitement. Pour plus d’informations, voir [Règles de traitement et données contextuelles](/help/android/getting-started/proc-rules.md).

Les valeurs que vous avez affectées directement aux variables doivent être ajoutées à la table de hachage HashMap `data`. Cela signifie que les appels vers `setProp`, `setEvar`, ainsi que les attributions à des données contextuelles persistantes, doivent être supprimés et les valeurs doivent être ajoutées au paramètre `data`.

## AppSection/server, GeoZip, transaction ID, Campaign et autres variables standard

Les données que vous définissiez dans l’objet de mesure, y compris les variables répertoriées ci-dessus, doivent être ajoutées à la table de hachage HashMap `data`. Les seules données envoyées avec un appel `trackState` ou `trackAction` sont la charge utile dans le paramètre `data`.

### Remplacement des appels de suivi

Remplacez les méthodes suivantes par un appel à `trackState` ou `trackAction` :

* **Migration depuis la version 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migration depuis la version 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Identifiant visiteur personnalisé {#section_2CF930C13BA64F04959846E578B608F3}

Remplacez la variable `visitorID` par un appel à `setUserIdentifier`.

## Suivi hors ligne {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Le suivi hors ligne est activé dans le fichier `ADBMobileConfig.json` et le reste de la configuration hors ligne est effectué automatiquement.

Supprimez les appels pour les méthodes suivantes :

**Version 3.x**

* `setOnline`
* `setOffline`

**Version 2.x**

* `forceOffline`
* `forceOnline`

## Variable products{#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Pour obtenir plus d’informations sur la variable products, voir [Variable products](/help/android/analytics-main/products/products.md).


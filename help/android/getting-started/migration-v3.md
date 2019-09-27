---
description: Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.
keywords: android;library;mobile;sdk
seo-description: Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.
seo-title: Migration vers la bibliothèque Android 4.x
solution: Marketing Cloud,Analytics
title: Migration vers la bibliothèque Android 4.x
topic: Développeur et mise en œuvre
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

Ces informations vous aident à migrer de la version 2.x ou 3.x de la bibliothèque Android vers la version 4.x.

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Si vous modifiez ou supprimez dans `SharedPreferences` des valeurs attendues par le SDK, il peut en résulter un comportement inattendu sous la forme de données incohérentes.

Dans la bibliothèque version 4.x, les méthodes publiques sont consolidées dans un en-tête. En outre, toutes les fonctionnalités sont désormais accessibles par des méthodes de niveau de classe : ainsi, il n’est pas nécessaire d’effectuer le suivi des pointeurs, des instances ou des singletons.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Dans la version 4, vous ne pouvez plus affecter des variables telles que les événements, les eVars, les props, les héritiers et les listes dans votre application. À la place, le SDK utilise des données contextuelles et des règles de traitement afin de faire correspondre les données de l’application aux variables Analytics à des fins de création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mises en correspondance à l’aide des règles de traitement.

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Les tableaux suivants répertorient les variables de configuration que vous devez déplacer vers le fichier de configuration.

### Déplacement du fichier de configuration

1. Déplacez la valeur définie pour la variable de la première colonne vers la variable de la deuxième colonne.
1. Supprimez l’ancienne variable de configuration du code.

### Migration depuis la version 3.x

Pour migrer de la version 3.x vers la version 4, déplacez la valeur de la variable/méthode de configuration vers la `ADBMobileConfig.json` variable.

| Variable ou méthode de configuration | Variable in the `ADBMobileConfig.json` file |
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

Pour migrer de la version 2.x à la version 4, déplacez la valeur de la première colonne vers la variable de la deuxième colonne.

| Variable de configuration | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the `"https://"` prefix. Le préfixe du protocole est ajouté automatiquement en fonction du paramètre "ssl". |
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
| useBestPractices  tous les appels à la mesure churn (getChurnInstance) | Supprimer, remplacé par Mesures de cycle de vie. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Au lieu d’utiliser les appels web `track` et `trackLink`, le SDK version 4 utilise les méthodes suivantes :

* `trackState`, qui sont les vues disponibles dans votre application, telles que `home dashboard`, `app settings`, `cart`, etc.

   Ces états sont semblables aux pages d’un site web ; les appels `trackState` incrémentent les pages vues.

* `trackAction` actions, telles que `logons`, `banner taps`, `feed subscriptions`, etc., qui se produisent dans votre application et que vous souhaitez mesurer.

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## Events, props, and eVars

Dans la version 4, vous ne pouvez plus affecter des variables telles que les événements, les eVars, les props, les héritiers et les listes directement dans votre application. Le SDK utilise désormais les données contextuelles et les règles de traitement pour faire correspondre les données de l’application aux variables Analytics pour la création de rapports.

Les avantages des règles de traitement sont les suivants :

* Vous pouvez modifier la correspondance de vos données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact.

   Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mises en correspondance à l’aide des règles de traitement. Pour plus d’informations, voir Règles de [traitement et Données](/help/android/getting-started/proc-rules.md)contextuelles.

Les valeurs que vous avez affectées directement aux variables doivent être ajoutées à la table de hachage HashMap `data`. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server, GeoZip, ID de transaction, Campaign et autres variables standard

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

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Supprimez les appels pour les méthodes suivantes :

**Version 3.x**

* `setOnline`
* `setOffline`

**Version 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).


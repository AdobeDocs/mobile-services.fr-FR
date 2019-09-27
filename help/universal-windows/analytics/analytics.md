---
description: valeur nulle
seo-description: valeur nulle
seo-title: Analytics
solution: Marketing Cloud,Analytics
title: Analytics
topic: Développeur et mise en œuvre
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application.

>[!TIP]
>
>Ensure that you import  to your class.`ADBMobile.h`

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Avant d’ajouter du code, demandez à votre administrateur Analytics de procéder comme suit pour activer le suivi du cycle de vie des applications mobiles. Cela garantit que la suite de rapports est prête à capturer des mesures lors du démarrage du développement.

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).

1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Cliquez sur **[!UICONTROL Activer la dernière version d’App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** or **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Les mesures de cycle de vie sont à présent capturées et les Rapports d’applications mobiles apparaissent dans le menu **Rapports** de l’interface des rapports marketing.

### Nouvelles versions

Périodiquement, de nouvelles versions des rapports d’applications mobiles sont publiées. Elles ne sont pas automatiquement appliquées à la suite de rapports. Vous devez répéter ces étapes pour effectuer la mise à niveau. Chaque fois que vous ajoutez une nouvelle fonctionnalité Experience Cloud à l’application, il est recommandé de répéter les étapes ci-dessus pour vous assurer de disposer de la dernière configuration.

## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

Pour collecter des mesures de cycle de vie dans l’application, ajoutez des appels lorsque l’application est activée, comme indiqué dans les exemples suivants. 

### WinJS dans default.js

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# dans App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C ++/CX dans App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

If `CollectLifecycleData()` is called twice in the same session, your application reports a crash on every call after the first. Le SDK définit un indicateur lorsque l’application est arrêtée afin de signaler une sortie réussie. If this flag is not set, `CollectLifecyleData()` reports a crash.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

If you've looked at [SDK methods](/help/universal-windows/c-configuration/methods.md), you are probably wondering where to set events, eVars, props, heirs, and lists. Dans la version 4, vous ne pouvez plus affecter ces types de variables directement dans l’application. À la place, le SDK utilise des données contextuelles et des règles de traitement afin de faire correspondre les données de l’application aux variables Analytics à des fins de création de rapports.

Les règles de traitement présentent plusieurs avantages :

* Vous pouvez modifier la correspondance des données sans soumettre de mise à jour dans la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires a très peu d’impact. Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne sont pas mappées à l’aide des règles de traitement.

Les valeurs que vous avez affectées directement aux variables doivent plutôt être ajoutées aux données contextuelles.

## Règles de traitement {#section_66EE762EEA5E4728864166201617DEBF}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des eVars, props et autres variables pour la création de rapports.

[Formation aux règles de traitement](https://tv.adobe.com/embed/1181/16506/) – Summit 2013

[Aide relative aux règles de traitement](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtention de l’autorisation d’utiliser des règles de traitement](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Il est recommandé de regrouper les variables de données contextuelles à l’aide d’espaces de noms, car cela vous aide à conserver un ordre logique. Si, par exemple, vous souhaitez collecter des informations sur un produit, vous pouvez définir les variables suivantes :

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement, afin que les espaces de noms permettent de voir rapidement les variables qui se trouvent dans le même espace de noms.

En outre, nous avons entendu dire que certains d’entre vous nomment des clés de données de contexte en utilisant le numéro d’eVar ou de prop :

```js
"eVar1":"jimbo"
```

Ceci pourrait *quelque peu* vous faciliter la tâche lorsque vous exécutez le mappage unique dans les règles de traitement, mais la lisibilité sera réduite au cours du débogage et des futures mises à jour de code, qui pourront alors s’avérer plus complexes. Il est vivement recommandé d’utiliser plutôt des noms explicites pour les clés et les valeurs :

```js
"username":"jimbo"
```

Définissez les variables contextuelles qui déterminent les événements de compteur sur la valeur "1" :

```js
"logon":"1"
```

Les variables de données contextuelles qui définissent les événements d’incrémenteur peuvent comporter la valeur à incrémenter :

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe réserve l’espace de noms `a.`. Outre cette restriction, les variables de données contextuelles doivent être uniques dans votre société de connexion pour éviter les collisions.

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Pour être défini *`products`* dans le SDK mobile, vous devez utiliser une syntaxe spéciale. Pour plus d’informations, voir Variable [](/help/universal-windows/analytics/products.md)Produits.

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [SDK methods](/help/universal-windows/c-configuration/methods.md) file. Soyez attentif aux exigences d’horodatage décrites dans la référence du fichier de configuration avant d’activer le suivi hors ligne.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

La géolocalisation permet de mesurer les données d’emplacement (latitude/longitude) et les points ciblés prédéfinis. Each `TrackLocation` call sends:

* Latitude/longitude et point ciblé (POI) (si dans un point ciblé défini dans le fichier de configuration `ADBMobileConfig.json`). 

   Ils sont transmis aux variables de la solution mobile pour la création de rapports automatique.

* Distance depuis le centre et exactitude transmises sous la forme de données contextuelles.

   Capture en utilisant une règle de traitement.

Pour effectuer le suivi d’un emplacement :

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Si le point ciblé (POI) suivant est défini dans le fichier de configuration `ADBMobileConfig.json` :

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

When the device location is determined to be within a 7000 meter radius of the defined point, an `a.loc.poi` context data variable with the value `San Francisco` is sent in with the `TrackLocation` hit. Une variable contextuelle `a.loc.dist` est envoyée avec la distance en mètres depuis les coordonnées définies.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

La valeur de durée de vie permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur. À chaque fois que vous envoyez une valeur avec `TrackLifetimeValueIncrease`, la valeur est ajoutée à la valeur existante. La valeur de durée de vie est stockée sur l’appareil et peut être récupérée à tout moment en appelant `GetLifetimeValue`. Cette procédure peut être utilisée pour stocker des valeurs de durée de vie (achats, vues des publicités, affichages complets de vidéos, partages sur les médias sociaux, chargement de photos, etc.).

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Les actions minutées permettent de mesurer la durée in-app et la durée totale écoulée entre le début et la fin d’une action. Le SDK calcule la durée de la session et la durée totale de toutes les sessions qu’il faudra pour que l’action soit terminée. Ces durées peuvent être utilisées pour définir des segments permettant de comparer la durée avant l’achat, le niveau de passage, le passage en caisse, etc.

* Nombre total de secondes dans l’application entre le début et la fin (intersessions)
* Nombre total de secondes entre le début et la fin (horloge)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```

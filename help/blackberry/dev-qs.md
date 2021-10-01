---
title: 'Développeurs : démarrage rapide'
description: Le guide de démarrage rapide du développeur BlackBerry vous aide à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry pour Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 6%

---

# Démarrage rapide pour les développeurs

Ces informations vous aident à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry.

## Obtention du kit SDK 

**Le SDK nécessite BlackBerry 10 ou une version ultérieure.**

Après avoir décompressé le SDK téléchargé, vérifiez que les fichiers suivants existent dans un dossier `AdobeMobile` :

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## Ajout des SDK à votre projet

1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Configurer]** > **[!UICONTROL Ajouter une bibliothèque]**.
1. Sélectionnez **[!UICONTROL Bibliothèque externe]** et cliquez sur **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Parcourir]** en regard du champ **[!UICONTROL Bibliothèque d’appareils]** .
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Dans le dossier `Device-Debug`, sélectionnez `libADBMobileShared.so` et cliquez sur **[!UICONTROL Ouvrir]**.
1. Cliquez sur **[!UICONTROL Parcourir]** en regard du champ **[!UICONTROL Bibliothèque du simulateur]** .
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Dans le dossier `Device-Debug`, sélectionnez `libADBMobileShared.so` et cliquez sur **[!UICONTROL Ouvrir]**.
1. Cliquez sur **[!UICONTROL Ajouter]** en regard du champ **[!UICONTROL Inclure les dossiers]** .
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Ajoutez le dossier `public` à vos inclusions.
1. Dans le dossier `ADBMobile-4.0.0BETA-BlackBerry`, il existe un fichier de configuration `.json` nommé `ADBMobileConfig.json`.

   Copiez ce fichier dans la racine de votre projet.
1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Actualiser]**.

   Le fichier `.json` doit maintenant être visible dans votre **[!UICONTROL Explorateur de projets]**.
1. Ouvrez le fichier `bar-descriptor.xml` correspondant à votre projet.
1. Au bas de la fenêtre, sélectionnez l’onglet **[!UICONTROL Ressources]** .
1. Vérifiez que **[!UICONTROL (Toutes les configurations)]** est sélectionné, puis cliquez sur **[!UICONTROL Ajouter des fichiers]** dans la section **[!UICONTROL Ressources]** de la fenêtre.
   >[!TIP]
   >
   >Il existe un bogue dans l’IDE QNX Momentics qui empêche parfois ces boutons d’être visibles. Si les boutons ne s’affichent pas, redimensionnez les fenêtres jusqu’à ce qu’elles apparaissent.

1. Cliquez sur **[!UICONTROL Espace de travail]**.
1. Recherchez le fichier `ADBMobileConfig.json` dans votre projet et cliquez sur **[!UICONTROL OK]**.

Votre application peut importer les classes/interfaces de la bibliothèque `adobeMobileLibrary.jar` à l’aide de `#include <ADBMobile.hpp>`.

## Ajout des autorisations des applications

Dans `bar-descriptor.xml` du répertoire du projet, ajoutez la ligne `<permission>access_internet</permission>` ou, dans l’IDE QNX Momentics, sélectionnez la zone **[!UICONTROL Internet]** dans la section des autorisations de l’onglet **[!UICONTROL Application]**.

## Mettre à jour le fichier de configuration `ADBMobileConfig.json`

Le fichier `ADBMobileConfig.json` contient les paramètres du SDK global. Vous devez mettre à jour quelques valeurs pour commencer.

Voici un exemple de fichier `ADBMobileConfig.json` :

```json
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
    }
}
```

Vous devez au moins mettre à jour les paramètres `rsids` et `server` . Pour plus d’informations, voir [Adobe de la classe mobile et référence des méthodes](/help/blackberry/methods.md).

Vous pouvez désormais mettre en oeuvre Analytics dans votre application BlackBerry 10.

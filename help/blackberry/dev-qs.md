---
title: 'Développeurs : démarrage rapide'
seo-title: BlackBerry Developer Quick Start pour Adobe Mobile Services
description: Le guide de démarrage rapide du développeur BlackBerry vous aide à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry pour Adobe Mobile Services.
seo-description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start

Ces informations vous permettent de comprendre le processus de mise en œuvre de la bibliothèque BlackBerry.

## Obtention du kit SDK

**BlackBerry version 10 ou ultérieure est requis par le SDK.**

Après avoir décompressé le SDK téléchargé, vérifiez que les fichiers ci-après existent dans un dossier `AdobeMobile` :

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

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Sélectionnez **[!UICONTROL Bibliothèque externe]**, puis cliquez sur **[!UICONTROL Suivant]**.
1. En regard du champ **[!UICONTROL Bibliothèque de l’appareil]**, cliquez sur **Parcourir[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. En regard du champ **[!UICONTROL Bibliothèque du simulateur]**, cliquez sur **Parcourir[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. En regard du champ **[!UICONTROL Inclure les dossiers], cliquez sur****Ajouter[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Ajoutez le dossier `public` à vos inclusions.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   Copiez ce fichier à la racine du projet.
1. Cliquez avec le bouton droit de la souris sur le projet, puis sélectionnez **[!UICONTROL Actualiser]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Ouvrez le fichier `bar-descriptor.xml` correspondant au projet.
1. Au bas de la fenêtre, sélectionnez l’onglet **[!UICONTROL Ressources].**
1. Vérifiez que l’option **[!UICONTROL (Toutes les configurations)]** est activée puis, dans la section **[!UICONTROL Ressources]de la fenêtre, cliquez sur** Ajouter des fichiers.****
   >[!TIP]
   >
   >There is a bug in the QNX Momentics IDE that sometimes prevents those buttons from being visible. Si vous ne voyez pas les boutons, redimensionnez les fenêtres jusqu'à ce qu'elles apparaissent.

1. Cliquez sur **[!UICONTROL Espace de travail]**.
1. Recherchez le fichier `ADBMobileConfig.json`**dans le projet, puis cliquez sur[!UICONTROL OK]**.

Votre application peut importer les classes/interfaces de la bibliothèque `adobeMobileLibrary.jar` à l'aide de `#include <ADBMobile.hpp>`.

## Add app permissions

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

Le fichier `ADBMobileConfig.json` contient les paramètres du SDK global. Pour commencer, certaines valeurs doivent être mises à jour.

Voici un exemple de fichier `ADBMobileConfig.json` :

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

You must at least update the `rsids` and `server` parameters. Pour plus d’informations, reportez-vous à la page Référence [de classe et de méthode](/help/blackberry/methods.md)Adobe Mobile.

Vous pouvez désormais mettre en œuvre Analytics dans votre application BlackBerry 10.

---
title: Début rapide des développeurs
seo-title: Début rapide des développeurs BlackBerry pour Adobe Mobile Services
description: Le guide de Début rapide des développeurs BlackBerry vous aide à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry pour Adobe Mobile Services.
seo-description: Le guide de Début rapide des développeurs BlackBerry vous aide à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry pour Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 5%

---


# Démarrage rapide pour les développeurs

Ces informations vous aident à comprendre le processus de mise en oeuvre de la bibliothèque BlackBerry.

## Obtention du kit SDK 

**Le SDK requiert BlackBerry 10 ou une version ultérieure.**

Après avoir décompressé le SDK téléchargé, vérifiez que les fichiers suivants existent dans un `AdobeMobile` dossier :

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

## Ajouter les SDK à votre projet

1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Configurer]** > Bibliothèque **[!UICONTROL d’]** Ajoutes.
1. Sélectionnez Bibliothèque **** externe et cliquez sur **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Parcourir]** en regard du champ de bibliothèque **** de périphériques.
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Dans le `Device-Debug` dossier, sélectionnez `libADBMobileShared.so` et cliquez sur **[!UICONTROL Ouvrir]**.
1. Cliquez sur **[!UICONTROL Parcourir]** en regard du champ de bibliothèque **** Simulator.
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Dans le `Device-Debug` dossier, sélectionnez `libADBMobileShared.so` et cliquez sur **[!UICONTROL Ouvrir]**.
1. Cliquez sur **[!UICONTROL Ajouter]** en regard du champ **[!UICONTROL Inclure les dossiers]** .
1. Accédez au dossier `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Ajoutez le `public` dossier à vos inclusions.
1. Dans le `ADBMobile-4.0.0BETA-BlackBerry` dossier, il existe un fichier `.json` de configuration nommé `ADBMobileConfig.json`.

   Copiez ce fichier dans la racine de votre projet.
1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Actualiser]**.

   Le `.json` fichier doit maintenant être visible dans l’Explorateur **[!UICONTROL de]** projets.
1. Ouvrez le `bar-descriptor.xml` fichier correspondant à votre projet.
1. Dans la partie inférieure de la fenêtre, sélectionnez l’onglet **[!UICONTROL Ressources]** .
1. Vérifiez que **[!UICONTROL (Toutes les configurations)]** est sélectionné, puis cliquez sur le bouton **[!UICONTROL Ajouter les fichiers]** dans la section **[!UICONTROL Ressources]** de la fenêtre.
   >[!TIP]
   >
   >Il y a un bogue dans l&#39;IDE QNX Momentics qui empêche parfois ces boutons d&#39;être visibles. Si les boutons ne s’affichent pas, redimensionnez les fenêtres jusqu’à ce qu’elles apparaissent.

1. Cliquez sur **[!UICONTROL Espace de travail]**.
1. Recherchez le `ADBMobileConfig.json` fichier dans votre projet, puis cliquez sur **[!UICONTROL OK]**.

Votre application peut importer les classes/interfaces de la `adobeMobileLibrary.jar` bibliothèque à l&#39;aide `#include <ADBMobile.hpp>`.

## Ajout des autorisations des applications

Dans `bar-descriptor.xml` le répertoire du projet, ajoutez la ligne `<permission>access_internet</permission>`ou dans l’IDE QNX Momentics, sélectionnez la zone **[!UICONTROL Internet]** dans la section permissions de l’onglet **[!UICONTROL Application]** .

## Mise à jour du fichier de `ADBMobileConfig.json` configuration

Le `ADBMobileConfig.json` fichier contient les paramètres du SDK global. Vous devez mettre à jour quelques valeurs pour commencer.

The following is an example of an `ADBMobileConfig.json` file:

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

Vous devez au moins mettre à jour les `rsids` paramètres et `server` . Pour plus d&#39;informations, reportez-vous à la section Référence [de classe et de méthode](/help/blackberry/methods.md)Adobe Mobile.

Vous pouvez désormais mettre en oeuvre Analytics dans votre application BlackBerry 10.

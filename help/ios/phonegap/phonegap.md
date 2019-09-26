---
description: Ce module permet d’envoyer des appels AppMeasurement pour iOS à partir de votre projet PhoneGap.
keywords: phonegap
seo-description: Ce module permet d’envoyer des appels AppMeasurement pour iOS à partir de votre projet PhoneGap.
seo-title: Module PhoneGap
solution: Marketing Cloud,Analytics
title: Module PhoneGap
topic: Développeur et mise en œuvre
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# PhoneGap plug-in{#phonegap-plug-in}

Ce module permet d’envoyer des appels AppMeasurement pour iOS à partir de votre projet PhoneGap.

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Création d’un projet PhoneGap

Pour créer un projet PhoneGap, voir [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Installation du module externe à l’aide de npm: {#section_43229E57C16944C0B51531CB92089189}

1. Exécutez la commande suivante :

   ```
   cordova plugin add adobe-mobile-services
   ```

## Installation manuelle du module externe {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Inclure la bibliothèque AppMeasurement

Pour inclure la bibliothèque AppMeasurement, procédez comme suit :

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. Procédez comme suit :

   1. Sélectionnez **[!UICONTROL Copier les éléments dans le dossier du groupe de destination (si nécessaire)]**.
   1. Sélectionnez les cibles dans lesquelles vous voulez utiliser le code AppMeasurement.

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Ajout d’autorisations d’application

La bibliothèque AppMeasurement exige de procéder comme suit :

1. Lancez Xcode IDE et ouvrez votre application.
1. Effectuez un glisser-déplacer du dossier **[!UICONTROL Adobe Mobile]vers votre projet Xcode, puis procédez comme suit :**

   1. Sélectionnez **[!UICONTROL Copier les éléments dans le dossier du groupe de destination (si nécessaire)]**.
   1. Sélectionnez **[!UICONTROL Créer des groupes pour les dossiers ajoutés]**.
   1. Sélectionnez les cibles dans lesquelles vous voulez utiliser le code AppMeasurement et cliquez sur **[!UICONTROL Terminer]**.
   ![](assets/xcode-settings.png){width="672"}

1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre projet, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```


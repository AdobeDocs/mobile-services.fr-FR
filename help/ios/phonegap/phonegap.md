---
description: Ce module externe permet d’envoyer des appels AppMeasurement pour iOS à partir de votre projet PhoneGap.
keywords: phonegap
solution: Experience Cloud Services,Analytics
title: Module externe PhoneGap
topic-fix: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
exl-id: c20b2f85-b8d4-47c7-8177-106c7ddfe083
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 100%

---

# Module externe PhoneGap {#phonegap-plug-in}

Ce module externe permet d’envoyer des appels AppMeasurement pour iOS à partir de votre projet PhoneGap.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Créer un projet PhoneGap

Pour créer un projet PhoneGap, voir [PhoneGap](https://helpx.adobe.com/fr/experience-manager/6-4/mobile/using/phonegap.html).

## Installation du module externe à l’aide de npm :  {#section_43229E57C16944C0B51531CB92089189}

1. Exécutez la commande suivante :

   ```
   cordova plugin add adobe-mobile-services
   ```

## Installation manuelle du module externe  {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Inclusion de la bibliothèque AppMeasurement

Pour inclure la bibliothèque AppMeasurement, procédez comme suit :

1. Faites glisser `ADBMobile_PhoneGap.h` et `ADBMobile_PhoneGap.m` dans le dossier **[!UICONTROL Plugins]** de votre projet Xcode.
1. Procédez comme suit :

   1. Sélectionnez **[!UICONTROL Copier les éléments dans le dossier du groupe de destination (si nécessaire)]**.
   1. Sélectionnez les cibles dans lesquelles vous voulez utiliser le code AppMeasurement.

1. Faites glisser `ADB_Helper.js` dans le dossier `www` de votre projet.
1. Dans le dossier `res/xml`, ouvrez `config.xml` et enregistrez un nouveau module externe en ajoutant ce qui suit :

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Ajout des autorisations des applications

La bibliothèque AppMeasurement requiert les éléments suivants :

1. Lancez Xcode IDE et ouvrez votre application.
1. Effectuez un glisser-déplacer du dossier **[!UICONTROL Adobe Mobile]** vers votre projet Xcode, puis procédez comme suit :

   1. Sélectionnez **[!UICONTROL Copier les éléments dans le dossier du groupe de destination (si nécessaire)]**.
   1. Sélectionnez **[!UICONTROL Créer des groupes pour les dossiers ajoutés]**.
   1. Sélectionnez les cibles dans lesquelles vous voulez utiliser le code AppMeasurement et cliquez sur **[!UICONTROL Terminer]**.

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre projet, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Mise en œuvre d’un suivi personnalisé {#section_FD102B3CDAA4492FB04E56BF17E28663}

Dans les fichiers `html` pour lesquels vous voulez utiliser le suivi, ajoutez le code ci-après à la balise `<head>` :

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

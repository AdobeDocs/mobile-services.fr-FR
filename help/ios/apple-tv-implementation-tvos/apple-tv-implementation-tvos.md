---
description: Ces informations vous permettent d’effectuer la mise en œuvre de l’Apple TV avec tvOS.
solution: Experience Cloud Services,Analytics
title: Mise en œuvre de l’Apple TV avec tvOS
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Mise en œuvre de l’Apple TV avec tvOS {#apple-tv-implementation-with-tvos}

Ces informations vous permettent d’effectuer la mise en œuvre de l’Apple TV avec tvOS.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aperçu

Avec Apple TV, vous pouvez désormais créer des applications s’exécutant dans l’environnement natif de tvOS. Vous pouvez créer une application native, à l’aide des différentes structures dans iOS, ou créer votre application à l’aide de modèles XML et de JavaScript.

>[!TIP]
>
>La prise en charge de tvOS est disponible à partir de la version 4.7.0 `AdobeMobileLibrary`.

## Prise en main {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Nous partons du principe que votre projet dispose d’une cible correspondant à une application Apple TV ciblant tvOS. Pour plus d’informations, voir [tvOS](https://developer.apple.com/tvos/documentation/).

## Configuration d’une application native pour tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier AdobeMobileLibrary dans votre projet.
1. Vérifiez que le fichier `ADBMobileConfig.json` est un membre de votre cible.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application tvOS, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Pour obtenir plus d’informations, consultez la documentation iOS sur [iOS](https://developer.apple.com/ios/resources/).

## Configuration d’une application TVML/TVJS pour tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Glissez-déposez le dossier `AdobeMobileLibrary` dans votre projet.
1. Vérifiez que le fichier `ADBMobileConfig.json` est un membre de votre cible.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application tvOS, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importez le SDK dans le fichier d’implémentation de votre classe `TVApplicationControllerDelegate`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Dans la méthode `application:didFinishLaunchWithOptions:` de votre classe `TVApplicationControllerDelegate`, transmettez votre objet `TVApplicationController` au SDK avec la méthode `installTVMLHooks:`.

   Le SDK Adobe requiert un accès au `TVApplicationController` de votre application pour s’inscrire dans le JSContext de votre application. Cette étape vous permet d’appeler des méthodes natives dans le SDK Adobe à partir de vos fichiers JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Dans vos fichiers JavaScript, utilisez l’objet `ADBMobile` pour accéder aux méthodes natives du SDK Adobe.

   Pour accéder à la liste complète des méthodes disponibles, voir [Méthodes TVJS](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

---
description: Ces informations vous permettent d’effectuer la mise en œuvre de l’Apple TV avec tvOS.
seo-description: Ces informations vous permettent d’effectuer la mise en œuvre de l’Apple TV avec tvOS.
seo-title: Mise en œuvre de l’Apple TV avec tvOS
solution: Marketing Cloud,Analytics
title: Mise en œuvre de l’Apple TV avec tvOS
topic: Développeur et mise en œuvre
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

Ces informations vous permettent d’effectuer la mise en œuvre de l’Apple TV avec tvOS.

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aperçu

Avec Apple TV, vous pouvez désormais créer des applications s’exécutant dans l’environnement natif de tvOS. Vous pouvez créer une application native en utilisant différentes structures d’iOS ou créer votre application à l’aide de modèles XML et de JavaScript.

>[!TIP]
>
>La prise en charge de tvOS est disponible à partir de la `AdobeMobileLibrary` version 4.7.0.

## Prise en main {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>We assume that your project has a target that is an Apple TV app that is targeting tvOS. Pour plus d’informations, voir [tvOS](https://developer.apple.com/tvos/documentation/).

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier AdobeMobileLibrary dans votre projet.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application tvOS, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Pour obtenir plus d’informations, consultez la documentation iOS sur [iOS](https://developer.apple.com/ios/resources/).

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Glissez-déposez le dossier `AdobeMobileLibrary` dans votre projet.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Dans l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application tvOS, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importez le SDK dans le fichier d’implémentation de votre classe `TVApplicationControllerDelegate`.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Le SDK Adobe requiert un accès au `TVApplicationController` de votre application pour s’inscrire dans le JSContext de votre application. Cette étape vous permet d’appeler des méthodes natives dans le SDK Adobe à partir de vos fichiers JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Dans vos fichiers JavaScript, utilisez l’objet `ADBMobile` pour accéder aux méthodes natives du SDK Adobe.

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).


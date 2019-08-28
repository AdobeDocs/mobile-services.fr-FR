---
description: Depuis iOS 10, Apple permet la création d’une extension autonome pouvant être distribuée sans application contenante. Grâce à cette extension, vous n’avez pas besoin d’un groupe d’applications, car l’application contenante avec laquelle partager les données est inexistante.
seo-description: Depuis iOS 10, Apple permet la création d’une extension autonome pouvant être distribuée sans application contenante. Grâce à cette extension, vous n’avez pas besoin d’un groupe d’applications, car l’application contenante avec laquelle partager les données est inexistante.
seo-title: Mise en œuvre d’une extension autonome
solution: Marketing Cloud, Analytics
title: Mise en œuvre d’une extension autonome
topic: Développeur et mise en œuvre
uuid: 9 b 47 f 082-b 78 f -4611-968 d -014 c 32 ede 6 bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

Depuis iOS 10, Apple permet la création d’une extension autonome pouvant être distribuée sans application contenante. Grâce à cette extension, vous n’avez pas besoin d’un groupe d’applications, car l’application contenante avec laquelle partager les données est inexistante.

>[!IMPORTANT]
>
>Pour utiliser des extensions autonomes, vous devez disposer du kit Mobile SDK version 4.13.0 ou ultérieure.

## Configuration de votre extension autonome pour une utilisation avec le SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Pour configurer votre extension autonome, procédez comme suit :

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. Reliez les bibliothèques et les structures suivantes :

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Dans le contrôleur d’affichage principal de votre extension, définissez le type d’extension sur `ADBMobileAppExtensionTypeStandAlone` dans le SDK avant d’achever toute activité en lien avec le SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

Voici quelques informations supplémentaires :

* Une valeur de données contextuelles supplémentaire (`a.RunMode`) a été ajoutée pour indiquer si les données proviennent de l’application contenante ou de votre extension :

   * `a.RunMode = Application`

      Cette valeur signifie que l’accès provient de l’application contenante.
   * `a.RunMode = Extension`

      Cette valeur signifie que l’accès provient de l’extension.

* Aucun appel de cycle de vie n’est déclenché sur les applications d’extension iOS.


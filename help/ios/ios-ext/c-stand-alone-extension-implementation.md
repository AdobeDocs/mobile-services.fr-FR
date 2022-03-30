---
description: A partir d’iOS 10, Apple vous permet de créer une extension appelée extension autonome qui peut être distribuée sans application contenante. Avec cette extension, vous n’avez pas besoin d’un groupe d’applications, car il n’existe aucune application contenante avec laquelle partager les données.
solution: Experience Cloud Services,Analytics
title: Mise en œuvre d’une extension autonome
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 100%

---

# Mise en œuvre d’une extension autonome  {#stand-alone-extension-implementation}

A partir d’iOS 10, Apple vous permet de créer une extension appelée extension autonome qui peut être distribuée sans application contenante. Avec cette extension, vous n’avez pas besoin d’un groupe d’applications, car il n’existe aucune application contenante avec laquelle partager les données.

>[!IMPORTANT]
>
>Pour utiliser des extensions autonomes, vous devez disposer du mobile SDK version 4.13.0 ou ultérieure.

## Configuration de votre extension autonome pour une utilisation avec le SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Pour configurer votre extension autonome, procédez comme suit :

1. Vérifiez que le fichier `ADBMobileConfig.json` est un membre de la cible de votre extension.
1. Reliez les bibliothèques et les structures suivantes :

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Dans le contrôleur d’affichage principal de votre extension, définissez le type d’extension sur `ADBMobileAppExtensionTypeStandAlone` dans le SDK avant d’achever toute activité en lien avec le SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Remarques supplémentaires {#section_1C9A55E2309A44BF842310F735702B3D}

Voici quelques informations supplémentaires :

* Une valeur de données contextuelles supplémentaire ( `a.RunMode` ) a été ajoutée pour indiquer si les données proviennent de l’application contenante ou de votre extension :

   * `a.RunMode = Application`

      Cette valeur signifie que l’accès provient de l’application contenante.
   * `a.RunMode = Extension`

      Cette valeur signifie que l’accès provient de l’extension.

* Aucun appel de cycle de vie n’est déclenché sur les applications de l’extension iOS.

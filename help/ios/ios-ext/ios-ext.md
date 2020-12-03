---
description: L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.
seo-description: L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.
seo-title: Mise en œuvre de l’extension iOS
solution: Experience Cloud,Analytics
title: Mise en œuvre de l’extension iOS
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 100%

---


# Mise en œuvre de l’extension iOS {#ios-extension-implementation}

L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recommandations d’utilisation du SDK iOS plutôt que votre propre wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Il est vivement recommandé d’utiliser le SDK iOS plutôt que votre propre wrapper.

Apple fournit un ensemble d’API qui permet à l’application Watch de communiquer avec l’application contenante en envoyant des requêtes à l’application contenante et en recevant les réponses. Bien que vous puissiez envoyer les données de suivi sous forme de dictionnaire de l’application Watch vers l’application contenante et appeler toute méthode de suivi sur l’application contenante pour envoyer les données, cette solution présente des limites.

Dans la plupart des cas, lorsqu’un utilisateur a recours à l’application Watch, l’application contenante s’exécute en arrière-plan et seules les méthodes `TrackActionInBackground`, `TrackLocation` et `TrackBeacon` peuvent être appelées en toute sécurité. L’appel d’autres méthodes de suivi interfère avec les données de cycle de vie. Vous devez donc utiliser uniquement ces trois méthodes pour envoyer les données depuis l’application Watch.

Même si ces trois méthodes de suivi répondent à vos besoins, il est recommandé d’utiliser le SDK iOS, car le SDK pour l’application Watch contient toutes les fonctionnalités mobiles, à l’exception des messages intégrés (in-app).

## Prise en main {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Vérifiez que l’un de vos projets comprend au minimum les cibles suivantes :
>
>* Une cible pour contenir l’application.
>* Une cible pour l’extension.

>



Si vous travaillez sur une application WatchKit, vous devriez avoir une troisième cible. Pour plus d’informations sur le développement pour Apple Watch, voir [Développement pour Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configuration de l’application conteneur {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier AdobeMobileLibrary dans votre projet.
1. Assurez-vous que le fichier `ADBMobileConfig.json` est membre de la cible de l’application contenante.
1. Sous l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application contenante, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Ouvrez l’onglet **[!UICONTROL Fonctionnalités]** de la cible de l’application contenante, activez l’option **[!UICONTROL Groupes d’applications]** et ajoutez un nouveau groupe d’applications (par exemple, `group.com.adobe.testAp`).

1. Dans le délégué de votre application, définissez le groupe d’applications dans `application:didFinishLaunchingWithOptions` avant toute interaction avec la bibliothèque Adobe Mobile :

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Configuration de l’extension {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Vérifiez que le fichier `ADBMobileConfig.json` est un membre de la cible de votre extension.
1. Sous l’onglet **[!UICONTROL Créer les phases]** de la cible de votre extension, développez la section **[!UICONTROL Lier le fichier binaire avec les bibliothèques]**, puis ajoutez les bibliothèques suivantes :

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Ouvrez l’onglet **[!UICONTROL Fonctionnalités]** de la cible de l’extension, activez l’option **[!UICONTROL Groupes d’applications]** et sélectionnez le groupe d’applications ajouté à l’étape 4 de la section *Configuration de l’application contenante* ci-dessus.

1. Dans votre InterfaceController, définissez le groupe d’applications dans `awakeWithContext:` avant toute interaction avec la bibliothèque Adobe Mobile :

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Remarques supplémentaires {#section_21497E81231549CB9F164DEECFF5BA0D}

Prenez note des informations suivantes :

* Une valeur de données contextuelles supplémentaire ( `a.RunMode` ) a été ajoutée pour indiquer si les données proviennent de l’application contenante ou de votre extension :

   * `a.RunMode = Application`

      Cette valeur signifie que l’accès provient de l’application contenante.
   * `a.RunMode = Extension`

      Cette valeur signifie que l’accès provient de l’extension.

* Si vous effectuez une mise à niveau à partir d’une ancienne version du SDK, lorsque l’application contenante est lancée, Adobe migre automatiquement tous les fichiers par défaut et mis en cache de l’utilisateur du dossier de l’application contenante au dossier partagé du groupe d’applications.
* Si l’application contenante n’est jamais lancée, les accès provenant de l’extension sont ignorés.
* Le numéro de version et le numéro de build doivent être identiques entre votre application contenante et l’application de l’extension.
* Aucun appel de cycle de vie n’est déclenché sur les applications de l’extension iOS.


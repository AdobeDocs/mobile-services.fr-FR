---
description: L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.
seo-description: L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.
seo-title: Mise en œuvre de l’extension iOS
solution: Marketing Cloud, Analytics
title: Mise en œuvre de l’extension iOS
topic: Développeur et mise en œuvre
uuid: 8 afc 03 fe -403 e -4643-ada 1-30 e 403 ede 238
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# iOS extension implementation {#ios-extension-implementation}

L’extension iOS permet de collecter les données d’utilisation de vos applications Apple Watch (WatchOS 1), de widgets quotidiens, de widgets de retouche de photos et autres extensions d’application iOS.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Nous vous recommandons vivement d'utiliser le SDK ios plutôt que votre enveloppe.

Apple fournit un ensemble d’API qui permet à l’application Watch de communiquer avec l’application contenante en envoyant des demandes à l’application contenante et en recevant des réponses. Bien que vous puissiez envoyer les données de suivi en tant que dictionnaire de l’application Watch à l’application contenante et appeler ensuite n’importe quelle méthode de suivi sur l’application contenante pour envoyer les données, cette solution est limitée.

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. L’appel d’autres méthodes de suivi interfère avec les données de cycle de vie. Vous devez donc utiliser uniquement ces trois méthodes pour envoyer les données depuis l’application Watch.

Même si ces trois méthodes de suivi répondent à vos besoins, il est recommandé d’utiliser le SDK iOS, car le SDK pour l’application Watch contient toutes les fonctionnalités mobiles, à l’exception des messages intégrés (in-app).

## Prise en main {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Assurez-vous d'avoir un projet avec au moins les cibles suivantes :
>
>* Une cible contenant l’application.
>* Une cible pour l’extension.
>



Si vous utilisez une application WatchKit, vous devez avoir une troisième cible. Pour plus d'informations sur le développement pour Apple Watch, voir [Développement pour Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configuration de l'application réceptrice {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Procédez comme suit dans votre projet Xcode :

1. Glissez-déposez le dossier AdobeMobileLibrary dans votre projet.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. Sous l’onglet **[!UICONTROL Créer les phases]** de la cible de votre application contenante, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. Dans le délégué de votre application, définissez le groupe d’applications dans `application:didFinishLaunchingWithOptions` avant toute interaction avec la bibliothèque Adobe Mobile :

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Configuration de l'extension {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. Sous l’onglet **[!UICONTROL Créer les phases]** de la cible de votre extension, développez la section **Lier le fichier binaire avec les bibliothèques], puis ajoutez les bibliothèques suivantes :[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Vérifiez qu’aucune erreur inattendue n’est générée lors de la création de votre application.

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

Prenez note des informations suivantes :

* Une valeur de données contextuelles supplémentaire (`a.RunMode`) a été ajoutée pour indiquer si les données proviennent de l’application contenante ou de votre extension :

   * `a.RunMode = Application`

      Cette valeur signifie que l’accès provient de l’application contenante.
   * `a.RunMode = Extension`

      Cette valeur signifie que l’accès provient de l’extension.

* Si vous effectuez une mise à niveau à partir d’une ancienne version du SDK, lorsque l’application contenante est lancée, Adobe migre automatiquement tous les paramètres utilisateur par défaut ainsi que les fichiers en cache depuis le dossier de l’application contenante vers le dossier partagé du groupe d’applications.
* Si l’application contenante n’est jamais lancée, les accès provenant de l’extension sont supprimés.
* Les numéros de version de l’application contenante et de l’application d’extension doivent être identiques.
* Aucun appel de cycle de vie n’est déclenché sur les applications d’extension iOS.


---
description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: Développeur et mise en œuvre
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.

Depuis iOS 9, Apple a introduit ATS, un ensemble d’exigences qui se conforme aux bonnes pratiques relatives à la sécurisation des connexions. Pour plus d’informations, voir *NSAppTransportSecurity* dans le Guide de référence [des clés de la liste des propriétés d’](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)informations.

Pour que le SDK Adobe Mobile version 4.7 ou supérieure fonctionne correctement avec ATS, vous devez activer le protocole SSL dans la page Gérer les paramètres d’application. Pour plus d’informations, voir [Gestion des paramètres](/help/using/c-manage-app-settings/c-manage-app-settings.md) d’application ou Configuration [JSON](/help/ios/configuration/json-config/json-config.md)ADBMobile.

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

As an alternative, you can whitelist service the following servers:

| Produit | Instructions |
|--- |--- |
| Analytics | Pour placer votre serveur Analytics sur liste blanche, ajoutez le domaine du serveur de suivi en tant que domaine d’exception pour ATS dans le fichier info.plist.  Le domaine du serveur de suivi se trouve dans la section Analytics du fichier `ADBMobileConfig.json` ou dans la section Analytics de la page Gérer les paramètres d’application. |
| Audience Manager | Votre domaine Audience Manager se trouve dans la propriété du serveur de l’objet audienceManager du fichier `ADBMobileConfig.json`.  Si vous utilisez Audience Manager dans votre application et que le protocole SSL est désactivé, ajoutez ce serveur en tant que domaine d’exception pour ATS dans votre fichier `Info.plist`. |
| Target | Vous pouvez ajouter votre point de terminaison Target à votre fichier Info.plist en tant que domaine d’exception pour ATS.  Pour trouver votre point de terminaison Target, localisez `clientCodeproperty` dans l’objet cible de votre fichier `ADBMobileConfig.json`. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | Vous pouvez ajouter le serveur Experience Cloud en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. This domain is `dpm.demdex.net`. |
| Mobile Services : acquisition | Ajoutez le serveur d’acquisition en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. This domain is `c00.adobe.com`. |
| Mobile Services : messages in-app | Si vous utilisez des messages in-app, il vous faudra peut-être ajouter des entrées dans le domaine d’exception pour ATS, pour chacune des URL que vous utilisez qui n’est pas basée sur le protocole HTTPS. Cette liste comprend des images hébergées et les URL incorporées dans votre HTML de messages plein écran personnalisés.  Pour plus d’informations sur la configuration du domaine des exceptions dans un `info.plist` fichier, voir la ligne *NSExceptionDomains* du *tableau 2 : Clés* primaires du dictionnaire de sécurité du transport d’application. Voir aussi *Tableau 3 Clés* de dictionnaire des domaines d’exception dans le Guide de référence [des clés de liste des propriétés](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)d’informations. |

>[!TIP]
>
>These considerations affect the connections that are made by the Adobe Mobile SDK and do not impact web view or other connections that are made by your app.


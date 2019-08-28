---
description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud, Analytics
title: App Transport Security
topic: Développeur et mise en œuvre
uuid: e 9 ee 13 cf -9802-492 e -8 b 11-95 f 028 e 34 e 61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.

Depuis iOS 9, Apple a introduit ATS, un ensemble d’exigences qui se conforme aux bonnes pratiques relatives à la sécurisation des connexions. Pour plus d'informations, voir *nsapptransportsecurity* dans [la référence de clé de la liste des propriétés d'informations](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Pour que le SDK Adobe Mobile version 4.7 ou supérieure fonctionne correctement avec ATS, vous devez activer le protocole SSL dans la page Gérer les paramètres d’application. Pour plus d'informations, voir [Gestion des paramètres d'application](/help/using/c-manage-app-settings/c-manage-app-settings.md) ou [Configuration JSON adbmobile](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

Vous pouvez d'autre part utiliser le service Liste blanche pour les serveurs suivants :

| Produit | Instructions |
|--- |--- |
| Analytics | Pour placer votre serveur Analytics sur liste blanche, ajoutez le domaine du serveur de suivi en tant que domaine d’exception pour ATS dans le fichier info.plist.  Le domaine du serveur de suivi se trouve dans la section Analytics du fichier `ADBMobileConfig.json` ou dans la section Analytics de la page Gérer les paramètres d’application. |
| Audience Manager | Votre domaine Audience Manager se trouve dans la propriété du serveur de l’objet audienceManager du fichier `ADBMobileConfig.json`.  Si vous utilisez Audience Manager dans votre application et que le protocole SSL est désactivé, ajoutez ce serveur en tant que domaine d’exception pour ATS dans votre fichier `Info.plist`. |
| Target | Vous pouvez ajouter votre point de terminaison Target à votre fichier Info.plist en tant que domaine d’exception pour ATS.  Pour trouver votre point de terminaison Target, localisez `clientCodeproperty` dans l’objet cible de votre fichier `ADBMobileConfig.json`. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | Vous pouvez ajouter le serveur Experience Cloud en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. This domain is `dpm.demdex.net`. |
| Mobile Services : acquisition | Ajoutez le serveur d’acquisition en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. This domain is `c00.adobe.com`. |
| Mobile Services : messages in-app | Si vous utilisez des messages in-app, il vous faudra peut-être ajouter des entrées dans le domaine d’exception pour ATS, pour chacune des URL que vous utilisez qui n’est pas basée sur le protocole HTTPS. Cette liste comprend des images hébergées et les URL incorporées dans votre HTML de messages plein écran personnalisés.  Pour plus de détails sur le paramétrage du domaine des exceptions à un `info.plist` fichier, voir la ligne *nsexceptiondomains* du *tableau 2 : Clés principales du dictionnaire de la sécurité de l'application*. Voir *également les clés du dictionnaire des domaines d'exception Tableau 3* dans [la référence de clé de la liste des propriétés d'informations](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Ces considérations affectent les connexions effectuées par le SDK Adobe Mobile et n'affectent pas l'affichage Web ou les autres connexions effectuées par votre application.


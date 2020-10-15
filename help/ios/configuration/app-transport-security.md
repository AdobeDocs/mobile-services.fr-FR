---
description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-description: Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.
seo-title: App Transport Security
solution: Experience Cloud,Analytics
title: App Transport Security
topic: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '486'
ht-degree: 100%

---


# App Transport Security {#app-transport-security}

Ces informations vous permettent de travailler avec App Transport Security (ATS), un nouvel ensemble d’exigences de sécurité pour iOS 9.

Depuis iOS 9, Apple a introduit ATS, un ensemble d’exigences qui se conforme aux bonnes pratiques relatives à la sécurisation des connexions. Pour plus d’informations, voir *NSAppTransportSecurity* dans [Référence de clé pour une liste de propriété d’informations](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Pour que le SDK Adobe Mobile version 4.7 ou supérieure fonctionne correctement avec ATS, vous devez activer le protocole SSL dans la page Gérer les paramètres d’application. Pour plus d’informations, voir [Gérer les paramètres d’application](/help/using/c-manage-app-settings/c-manage-app-settings.md) ou [Configuration ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

Dans Adobe Mobile Services, si vous activez l’option **[!UICONTROL Utiliser HTTPS]** sur la page Gérer les paramètres d’application, tous les accès issus d’Analytics, d’Audience Manager, de Target et des services Adobe Experience Platform sont envoyés par HTTPS.

Vous pouvez également placer les serveurs suivants dans votre liste de serveurs « autorisés » :

| Produit | Instructions |
|--- |--- |
| Analytics | Pour autoriser votre serveur Analytics, ajoutez le domaine du serveur de suivi en tant qu’exception pour ATS dans le fichier info.plist.  Le domaine du serveur de suivi se trouve dans la section Analytics du fichier `ADBMobileConfig.json` ou dans la section Analytics de la page Gérer les paramètres d’application. |
| Audience Manager | Votre domaine Audience Manager se trouve dans la propriété du serveur de l’objet audienceManager du fichier `ADBMobileConfig.json`.  Si vous utilisez Audience Manager dans votre application et que le protocole SSL est désactivé, ajoutez ce serveur en tant que domaine d’exception pour ATS dans votre fichier `Info.plist`. |
| Target | Vous pouvez ajouter votre point de terminaison Target à votre fichier Info.plist en tant que domaine d’exception pour ATS.  Pour trouver votre point de terminaison Target, localisez `clientCodeproperty` dans l’objet cible de votre fichier `ADBMobileConfig.json`. Votre point de terminaison sera le suivant : `https://{clientCode}.tt.omtrdc.net`.  Par exemple, si votre `clientCodeproperty` est `“myCompany”`, votre point de terminaison sera `https://myCompany.tt.omtrdc.net`. |
| Service Adobe Experience Platform Identity | Vous pouvez ajouter le serveur Experience Cloud en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. Ce domaine est le suivant : `dpm.demdex.net`. |
| Mobile Services : acquisition | Autorisez le serveur d’acquisition en tant que domaine d’exception pour ATS dans le fichier `Info.plist`. Ce domaine est le suivant : `c00.adobe.com`. |
| Mobile Services : messages in-app | Si vous utilisez des messages in-app, vous devrez peut-être ajouter des entrées dans le domaine d’exception pour ATS pour chaque URL que vous utilisez qui n’est pas en HTTPS. Cette liste comprend des images hébergées et les URL incorporées dans votre HTML de messages plein écran personnalisés.  Pour plus d’informations sur la configuration du domaine d’exception dans un fichier `info.plist`, voir la ligne *NSExceptionDomains* du *Tableau 2 : Clés primaires du dictionnaire de sécurité du transport d’application*. Voir aussi *Tableau 3 : Clés du dictionnaire de domaines d’exception* dans [Référence de clé pour une liste de propriété d’informations](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Ces considérations affectent les connexions établies par le SDK Adobe Mobile. Elles n’ont pas d’incidence sur l’affichage Web ni sur d’autres connexions établies par votre application.


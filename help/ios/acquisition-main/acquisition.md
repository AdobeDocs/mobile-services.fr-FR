---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-title: Acquisition d’applications mobiles
solution: Marketing Cloud,Analytics
title: Acquisition d’applications mobiles
topic: Développeur et mise en œuvre
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.

Vous **devez** disposer d’un SDK version 4.1 ou ultérieure pour utiliser l’acquisition.

Les liens d’acquisition doivent être créés dans Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

Les informations de cette section permettent au SDK d’envoyer des données d’acquisition à partir d’un lien d’acquisition.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   > Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d’acquisition (serveur d’acquisition et appid) provenant de l’application associée à la première suite de rapports de la liste d’identifiants des suites de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

Lorsque ces paramètres sont activés, les données d’acquisition sont automatiquement envoyées avec l’appel de cycle de vie initial après le lancement initial de l’application.

>[!CAUTION]
>
>`referrerTimeout`  Pour activer l’acquisition d’applications,  doit être défini sur une valeur supérieure à 0.

## Enabling your iOS app for Universal Links

Si vous utilisez des liens universels dans votre application, ajoutez votre domaine Liens marketing Adobe à la liste Domaines associés pour votre application.

In Xcode, to add your Adobe Marketing Links domain to the Associated Domains list:

1. Go to your project target and click the Capabilities tab.****
2. Scroll down to Associated Domains section and toggle it on.****
3. Add an entry in the Domains list for your Marketing Links domain from your Marketing Links URL.****

Ton entrée ressemblera à quelque chose `applinks:5848561889a02a6996aea62b.c00.adobe.com`.
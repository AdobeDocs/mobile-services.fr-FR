---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-title: Acquisition d'applications mobiles
solution: Marketing Cloud, Analytics
title: Acquisition d'applications mobiles
topic: Développeur et mise en œuvre
uuid: 5 fece 619-e 4 b 8-4 d 06-9250-dcb 66 fa 32 ce 0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.

Vous **devez** disposer d’un SDK version 4.1 ou ultérieure pour utiliser l’acquisition.

Les liens d’acquisition doivent être créés dans Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

Les informations contenues dans cette section permettent au SDK d'envoyer des données d'acquisition à partir d'un lien d'acquisition.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/dev-qs.md).
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
   >Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d'acquisition (serveur d'acquisition et appid) de l'application associée à la première suite de rapports dans la liste des ID de suite de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

Lorsque ces paramètres sont activés, les données d’acquisition sont automatiquement envoyées avec l’appel de cycle de vie initial après le lancement initial de l’application.

>[!CAUTION]
>
>`referrerTimeout` doit être définie sur une valeur supérieure à 0 pour activer l'acquisition de l'application.

## Activation de l'application ios pour les liens universels

Si vous utilisez des liens universels dans votre application, ajoutez votre domaine Liens marketing Adobe à la liste Domaines associés de votre application.

Dans Xcode, pour ajouter votre domaine Liens marketing Adobe à la liste Domaines associés :

1. Accédez à la cible de votre projet et cliquez sur l'onglet **[!UICONTROL Fonctionnalités]** .
2. Faites défiler la section jusqu'à **[!UICONTROL la]** section Domaines associés et activez-la.
3. Ajoutez une entrée dans la liste **[!UICONTROL Domaines]** de votre domaine Liens marketing à partir de l'URL de liens marketing.

Votre entrée ressemble à ce qui `applinks:5848561889a02a6996aea62b.c00.adobe.com`suit.
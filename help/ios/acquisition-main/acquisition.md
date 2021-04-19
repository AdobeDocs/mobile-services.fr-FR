---
description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-description: Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.
seo-title: Acquisition des applications mobiles
solution: Experience Cloud,Analytics
title: Acquisition des applications mobiles
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 100%

---

# Acquisition des applications mobiles {#mobile-app-acquisition}

Il est possible de générer des liens d’acquisition avec des codes de suivi uniques dans Adobe Mobile Services. Lorsqu’un utilisateur télécharge et exécute une application à partir de l’App Store d’Apple après avoir cliqué sur le lien généré, le SDK collecte et envoie automatiquement les données d’acquisition à Adobe Mobile Services.

Pour utiliser Acquisition, vous **devez** disposer de la version 4.1 ou supérieure du SDK.

Les liens Acquisition doivent être créés dans Adobe Mobile Services. Pour en savoir plus, consultez la rubrique [Acquisition](/help/using/acquisition-main/acquisition-main.md).

Les informations de cette section permettent au SDK d’envoyer les données d’acquisition depuis un lien d’acquisition.

## Suivi de l’acquisition des applications mobiles {#section_CEA30C652AC8470784B8054E299B80FA}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vérifiez que le fichier `ADBMobileConfig.json` comporte les paramètres d’acquisition requis :

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
   >Si vous envoyez des données à plusieurs suites de rapports, utilisez les paramètres d’acquisition (serveur d’acquisition et appid) provenant de l’application associée à la première suite de rapports de la liste d’identifiants des suites de rapports.

   Les paramètres `acquisition` sont générés par Adobe Mobile Services et ne doivent pas être modifiés. Pour obtenir plus d’informations sur le mode de téléchargement d’un fichier `ADBMobileConfig.json` personnalisé avec les paramètres `acquisition` préconfigurés, voir [Avant de démarrer](/help/ios/getting-started/requirements.md).

Lorsque ces paramètres sont activés, les données d’acquisition sont automatiquement envoyées avec l’appel de cycle de vie initial après le lancement initial de l’application.

>[!CAUTION]
>
>Pour activer l’acquisition d’applications, `referrerTimeout` doit être défini sur une valeur supérieure à 0.

## Activation de votre application iOS pour les liens universels

Si vous utilisez des liens universels dans votre application, ajoutez votre domaine Liens marketing Adobe à la liste Domaines associés pour votre application.

Dans Xcode, pour ajouter votre domaine Liens marketing Adobe à la liste Domaines associés :

1. Accédez à la cible du projet et cliquez sur l’onglet **[!UICONTROL Fonctionnalités]**.
2. Faites défiler l’écran jusqu’à la section **[!UICONTROL Domaines associés]** et activez-la.
3. Ajoutez une entrée dans la liste **[!UICONTROL Domaines]** pour votre domaine Liens marketing à partir de l’URL des liens marketing.

Votre entrée ressemblera à `applinks:5848561889a02a6996aea62b.c00.adobe.com`.

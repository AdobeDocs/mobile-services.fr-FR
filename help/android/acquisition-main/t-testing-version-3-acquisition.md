---
description: Ces informations vous expliquent comment rediriger un lien de campagne Acquisition version 3 sur un appareil Android.
keywords: android;library;mobile;sdk
seo-description: Ces informations vous expliquent comment rediriger un lien de campagne Acquisition version 3 sur un appareil Android.
seo-title: Test d’Acquisition version 3
solution: Experience Cloud,Analytics
title: Test d’Acquisition version 3
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 85%

---


# Test de l’acquisition de V3 {#testing-version-acquisition}

Ces informations vous expliquent comment rediriger un lien de campagne Acquisition version 3 sur un appareil Android.

>[!IMPORTANT]
>
>L’acquisition dans V 3 fait référence aux liens d’acquisition que vous créez avec le Créateur d’acquisitions dans l’interface utilisateur Adobe Mobile Services. Pour utiliser cette fonctionnalité, vous devez effectuer la mise à niveau vers Android SDK 4.x pour les solutions Experience Cloud 4.6.0 ou versions ultérieures.

Si l’application mobile n’est pas encore dans Google Play, lors de la création du lien de la campagne, vous pouvez sélectionner n’importe quelle application mobile comme destination. Seule l’application vers laquelle le serveur d’acquisition vous redirige après avoir cliqué sur le lien d’acquisition est concernée. Le lien pourra toujours être testé. Les paramètres de chaîne de requête sont transmis à la boutique Google Play, qui sont transmis à l’application lors de l’installation dans le cadre d’une diffusion de campagne. Les tests d’acquisition d’applications mobiles nécessitent la simulation de ce type de diffusion.

>[!IMPORTANT]
>
>Si vous effectuez une implémentation à l’aide des API de référents d’installation de Google Play, vous ne pouvez pas tester l’acquisition avant que votre application ne se trouve dans la boutique Google Play.

Chaque fois qu’un test est exécuté, l’application doit avoir été installée depuis peu ou ses données doivent être effacées sous **[!UICONTROL Paramètres]**. Ainsi, les mesures initiales de cycle de vie associées aux paramètres des chaînes de requête de la campagne sont envoyées lorsque l’application est lancée pour la première fois.

1. Effectuez les tâches préalables requises dans [Acquisition des applications mobiles](/help/android/acquisition-main/acquisition.md) et assurez-vous que vous avez correctement mis en œuvre le récepteur de diffusion pour `INSTALL_REFERRER`.

1. Dans l’interface utilisateur d’Adobe Mobile Services, cliquez sur **[!UICONTROL Acquisition]** > **[!UICONTROL Générateur de liens marketing]**, puis générez une URL de lien marketing d’acquisition qui définit Google Play comme destination des appareils Android.

   Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Par exemple : `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Si vous vous référez à la fois aux applications Android et aux applications iOS dans le lien d’acquisition, utilisez Google Play comme boutique par défaut.

1. Ouvrez le lien généré dans un navigateur de bureau.

   Vous devez être redirigé vers une page dont l’URL est similaire à l’exemple suivant :
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copiez l’identifiant unique après `utm_content%3D`.

   Dans l’exemple précédent, l’ID est `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Créez le lien de fin de l’acquisition en utilisant l’identifiant unique de l’étape 3, avec le format suivant :

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Par exemple : `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Ouvrez le lien généré dans un navigateur de bureau.

   `contextData` devrait apparaître dans la réponse JSON :

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Si `contextData` n’apparaît pas ou si certaines chaînes sont manquantes, assurez-vous que l’URL d’acquisition adopte le format indiqué dans le document [Création manuelle d’un lien d’acquisition](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Répétez l’étape 3 pour obtenir un nouvel identifiant unique.
1. Vérifiez que les paramètres suivants du fichier de configuration sont corrects :

   | Paramètre | Valeur |
   |--- |--- |
   | acquisition | Le serveur doit être `c00.adobe.com`. *`appid`* doit être égal à l’`appid` de votre lien d’acquisition. |
   | analytics | À des fins de test, définissez le délai d’expiration du parrain pour permettre l’envoi manuel de la diffusion pendant une durée suffisante (60 secondes ou plus). Vous pouvez restaurer le paramètre d’expiration d’origine après le test. |

1. Connectez l’appareil à un ordinateur, désinstallez puis réinstallez l’application.
1. Lancez l’interpréteur de commandes ADB, puis l’application sur l’appareil.
1. Envoyez une diffusion en utilisant la commande `adb` suivante :

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Procédez comme suit :
   1. Remplacez `com.adobe.android` par le nom de module de votre application.
   1. Remplacez la référence du récepteur par celle de l’emplacement du récepteur de suivi de la campagne dans l’application.
   1. Remplacez les valeurs associées à `utm_content`.

   Si la diffusion est réussie, vous pouvez vous attendre à une réponse similaire à l’exemple suivant :

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (Facultatif) Vous pouvez activer la journalisation du débogage du SDK pour obtenir des informations supplémentaires.

   Si tout fonctionne correctement, les journaux suivants devraient être disponibles :

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Si vous ne voyez pas les journaux ci-dessus, vérifiez que vous avez suivi les étapes 6 à 12.

Le tableau suivant contient des informations supplémentaires sur les erreurs possibles :

| Erreur | Description |
|--- |--- |
| Analytics - Unable to decode response(*String*). | La réponse est incorrecte. |
| Analytics - Unable to parse response (*a JSON Response*). | La chaîne JSON est incorrecte. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | Absence du paramètre contextData dans la réponse. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` n’est pas inclus dans contextData. |
| Analytics - Acquisition referrer timed out. | Échec d’obtention de la réponse dans la durée définie par `referrerTimeout`. Augmentez la valeur et réessayez.  Assurez-vous également d’avoir ouvert le lien d’acquisition avant d’installer l’application. |

À noter :

* Les accès envoyés depuis l’application peuvent être surveillés à l’aide d’outils de surveillance HTTP afin de vérifier l’attribution de l’acquisition.
* Pour obtenir plus d’informations sur le mode de diffusion de `INSTALL_REFERRER`, voir [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns) (Test de la mesure des campagnes Google Play) dans le guide des développeurs Google.

* Un correctif de bogue a été publié pour l’acquisition sur Android 4.8.2.

   Avant de tester, mettez à niveau le SDK vers la dernière version.

* Vous pouvez utiliser l’outil Java `acquisitionTest.jar` fourni pour vous aider à obtenir l’identifiant unique et le référent d’installation de la diffusion qui, en retour, vous aident à obtenir les informations des étapes 3 à 12.

   **Installation de l’outil Java**

Pour installer l’outil Java, procédez comme suit :

1. Téléchargez le fichier [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip).

1. Extrayez le fichier .jar.

   Vous pouvez exécuter le fichier sur la ligne de commande.

   Par exemple :

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```

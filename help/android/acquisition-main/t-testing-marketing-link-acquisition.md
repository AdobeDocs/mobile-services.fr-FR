---
description: Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing sur un périphérique Android.
keywords: android ; library ; mobile ; sdk
seo-description: Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing sur un périphérique Android.
seo-title: Évaluation de l’acquisition d’un lien marketing
solution: Marketing Cloud, Analytics
title: Évaluation de l’acquisition d’un lien marketing
topic: Développeur et mise en œuvre
uuid: d 0933 dcc -8 fc 3-4 f 60-987 f -7 a 54559 aacf 5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing sur un périphérique Android.

Si votre application mobile n'est pas encore dans Google Play, vous pouvez sélectionner n'importe quelle application mobile comme destination lors de la création du lien marketing. Une fois que vous avez cliqué sur le lien d’acquisition, seule l’application vers laquelle le serveur d’acquisition vous redirige est affectée, et non la capacité à tester le lien d’acquisition. Les paramètres de chaîne de requête sont transmis à la boutique Google Play, puis à l’application lors de l’installation dans le cadre d’une diffusion de campagne. Le test aller-retour de l’acquisition de l’application mobile requiert la simulation de ce type de diffusion.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. Ainsi, les mesures initiales de cycle de vie associées aux paramètres des chaînes de requête de la campagne sont envoyées lorsque l’application est lancée pour la première fois.

1. Effectuez les tâches préalables requises dans [l'acquisition](/help/android/acquisition-main/acquisition.md) d'applications mobiles et assurez-vous d'avoir correctement mis en œuvre le destinataire de la diffusion.`INSTALL_REFERRER`
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Par exemple :

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Ouvrez le lien généré sur l’appareil Android.

   Vous devez être redirigé vers une page dont l’URL est similaire à l’exemple suivant :

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   Dans l'exemple précédent, l'identifiant est `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Si vous ne parvenez pas à obtenir l’identifiant unique sur l’appareil, exécutez la commande `CURL` suivante sur votre ordinateur pour obtenir l’identifiant unique depuis la chaîne de réponse.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Par exemple :

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Créez le lien de fin de l’acquisition en utilisant l’identifiant unique de l’étape 3, avec le format suivant : 

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   For example, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Ouvrez le lien dans un navigateur.

   `contextData` devrait apparaître dans la réponse JSON :

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Répétez l’étape 3 pour obtenir un nouvel identifiant unique.
1. Vérifiez que les paramètres suivants du fichier de configuration sont corrects : 

   | Paramètre | Valeur |
   |--- |--- |
   | acquisition | Le serveur doit être et `c00.adobe.com`*`appid`* doit être égal à `appid` dans le lien d'acquisition. |
   | analytics | À des fins de test, définissez le délai d’expiration du référent afin que la durée soit suffisante (60 secondes ou moins) pour permettre l’envoi manuel de la diffusion. Vous pouvez restaurer le délai d’expiration d’origine après le test. |

1. Connectez l’appareil à un ordinateur, désinstallez puis réinstallez l’application.
1. Lancez l’interpréteur de commandes ADB, puis l’application sur l’appareil.

   ```
   adb shell
   ```

1. Envoyez une diffusion en utilisant la commande `adb` suivante : 

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Remplacez `com.adobe.android` par le nom de module de votre application, remplacez la référence du récepteur par celle de l’emplacement du récepteur de suivi de la campagne dans l’application, puis remplacez les valeurs associées par `utm_content`.

   Si la diffusion est réussie, vous pouvez vous attendre à une réponse similaire à l’exemple suivant :

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Facultatif) Vous pouvez activer la journalisation du débogage du SDK pour obtenir des informations supplémentaires.

   Si tout fonctionne correctement, les journaux suivants devraient être disponibles :

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Sinon, assurez-vous que vous avez exécuté les étapes 6 à 10.

   Le tableau suivant répertorie les informations supplémentaires sur les erreurs possibles :

   | Erreur | Description |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | La réponse est incorrecte. |
   | Analytics - Unable to parse response (`a JSON Response`). | La chaîne JSON est incorrecte. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | Absence du paramètre `contextData` dans la réponse. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` n'est pas incluse dans contextdata. |
   | Analytics - Acquisition referrer timed out. | Échec d’obtention de la réponse dans la durée définie par `referrerTimeout`. Augmentez la valeur et réessayez.  Assurez-vous que vous avez ouvert le lien d’acquisition avant d’installer l’application. |

Gardez à l’esprit les informations suivantes :

* Les accès qui sont envoyés depuis l’application peuvent être surveillés à l’aide des outils de surveillance HTTP afin de vérifier l’attribution de l’acquisition.
* Pour obtenir plus d’informations sur le mode de diffusion de `INSTALL_REFERRER`, voir [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns) (Test de la mesure des campagnes Google Play) dans le guide des développeurs Google.
* Vous pouvez utiliser l’outil Java `acquisitionTest.jar` fourni pour vous aider à obtenir l’identifiant unique et le référent d’installation de la diffusion qui, en retour, vous aident à obtenir les informations des étapes 3 à 10.

**Installation de l'outil Java**

Pour installer l’outil Java, procédez comme suit :

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. Extrayez le fichier .jar.

   Vous pouvez exécuter le fichier .jar sur la ligne de commande.

Par exemple :

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

Les liens marketing sont mis en cache sur le serveur avec une durée d'expiration de dix minutes. Lorsque vous modifiez les liens marketing, vous devez attendre environ 10 minutes que les modifications soient prises en compte pour pouvoir à nouveau utiliser les liens.

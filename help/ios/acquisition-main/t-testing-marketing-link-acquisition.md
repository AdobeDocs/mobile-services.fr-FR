---
description: Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing basé sur l'empreinte d'un périphérique.
keywords: android ; library ; mobile ; sdk
seo-description: Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing basé sur l'empreinte d'un périphérique.
seo-title: Test de l'acquisition des liens marketing
solution: Marketing Cloud, Analytics
title: Test de l'acquisition des liens marketing
topic: Développeur et mise en œuvre
uuid: 69503 e 01-182 d -44 c 6-b 0 fb-e 1 c 012 ffa 3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Les instructions suivantes vous aident à aller chercher une campagne d'acquisition avec un lien marketing basé sur l'empreinte d'un périphérique.

1. Effectuez les tâches préalables requises dans [l'acquisition d'applications mobiles](/help/ios/acquisition-main/acquisition.md).
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   Par exemple :

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   L’élément contextData doit être indiqué dans la réponse JSON :

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Vérifiez que les paramètres suivants du fichier de configuration sont corrects : 

   | Paramètre | Valeur |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` doit être égal à *`appid`* dans le lien d'acquisition. |
   | analytics | La valeur de `referrerTimeout` doit être supérieure à 0. |

1. (Conditionnel) Si le paramètre SSL de votre fichier de configuration d’application est défini sur `false`, mettez votre lien d’acquisition à jour de façon à utiliser le protocole HTTP plutôt que le protocole HTTPS.
1. Cliquez sur le lien créé sur le périphérique mobile sur lequel vous souhaitez installer l’application.

   Les serveurs d’Adobe (`c00.adobe.com`) enregistrent l’empreinte numérique et vous redirigent vers l’App Store. Il n’est pas nécessaire de télécharger l’application pour effectuer les tests.
1. Lancez l’application pour la première fois à partir du même périphérique mobile que celui utilisé à l’étape 6.

   Si nécessaire, supprimez puis réinstallez l’application.
1. (Facultatif) Activez la journalisation de débogage du SDK pour obtenir des informations supplémentaires.

   Si tout fonctionne correctement, les journaux suivants devraient être disponibles :

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Si vous ne voyez pas ces journaux, vérifiez que vous avez terminé les étapes 4 et 5.

   Voici quelques informations sur les erreurs possibles :

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Une erreur de réseau s’est produite.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Le format de la réponse est incorrect.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      La réponse ne contient pas de paramètre `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` n'est pas inclus `contextData`dans.

   * `Analytics - Acquisition referrer timed out`

      Échec de récupération de la réponse dans le délai défini dans `referrerTimeout`. Augmentez la valeur et réessayez. Vérifiez également que vous avez ouvert le lien d’acquisition avant d’installer l’application et que vous utilisez le même réseau lorsque vous cliquez sur l’URL et que vous ouvrez l’application.

Prenez note des informations suivantes :

* Le serveur d’acquisition fournit une correspondance d’attribution basée sur l’adresse IP et les informations agent-utilisateur enregistrées lorsque vous cliquez sur le lien (étape 6) et lors du lancement de l’application (étape 7).

   Le réseau utilisé lorsque vous cliquez sur l’URL et lorsque vous ouvrez l’application doit être le même.

* En utilisant des outils de surveillance HTTP, les accès envoyés à partir de l’application peuvent être contrôlés pour vérifier l’attribution d’acquisition.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* Des variations dans l’agent-utilisateur envoyé peuvent provoquer l’échec de l’attribution.

   Assurez-vous d' `https://c00.adobe.com/v3/<appid>/start``https://c00.adobe.com/v3/<appid>/end` avoir les mêmes valeurs d'agent utilisateur.

* Le lien d’acquisition et l’accès du SDK doivent utiliser le même protocole HTTP/HTTPS.

   Si le lien et l'accès utilisent différents protocoles, où, par exemple, le lien utilise HTTP et que le SDK utilise HTTPS, l'adresse IP peut différer sur certains opérateurs pour chaque requête. Cela peut provoquer l’échec de l’attribution.

* Les liens marketing sont mis en cache sur le serveur avec une durée d'expiration de dix minutes.

   Lorsque vous apportez des modifications aux liens marketing, patientez environ 10 minutes avant d'utiliser les liens.
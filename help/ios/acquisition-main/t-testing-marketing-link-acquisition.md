---
description: Les instructions suivantes expliquent comment gérer une campagne d’acquisition avec un lien marketing basé sur l’empreinte numérique d’un périphérique.
keywords: android;library;mobile;sdk
seo-description: Les instructions suivantes expliquent comment gérer une campagne d’acquisition avec un lien marketing basé sur l’empreinte numérique d’un périphérique.
seo-title: Évaluation de l’acquisition d’un lien marketing
solution: Experience Cloud,Analytics
title: Évaluation de l’acquisition d’un lien marketing
topic-fix: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
exl-id: 2fb02b36-172e-4c16-9ef9-13f8288ab8a4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 100%

---

# Évaluation de l’acquisition d’un lien marketing {#testing-marketing-link-acquisition}

Les instructions suivantes expliquent comment gérer une campagne d’acquisition avec un lien marketing basé sur l’empreinte numérique d’un périphérique.

1. Effectuez les tâches préalables requises dans [Acquisition des applications mobiles](/help/ios/acquisition-main/acquisition.md).
1. Dans l’interface utilisateur Adobe Mobile Services, cliquez sur **[!UICONTROL Générateur de liens marketing]**, puis générez une URL de lien marketing d’acquisition définissant l’App Store en tant que destination pour les appareils iOS.

   Par exemple :

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Ouvrez le lien créé sur un appareil iOS, puis ouvrez `https://c00.adobe.com/v3/<appid>/end`.

   L’élément contextData doit être indiqué dans la réponse JSON :

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Vérifiez que les paramètres suivants du fichier de configuration sont corrects :

   | Paramètre | Valeur |
   |--- |--- |
   | acquisition | Le serveur doit être `c00.adobe.com`. `appid` doit être égal à l’*`appid`* de votre lien d’acquisition. |
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

   Si ces journaux ne s’affichent pas, vérifiez que vous avez bien effectué les étapes 4 et 5 de la procédure.

   Voici quelques informations sur les erreurs possibles :

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`

      Une erreur de réseau s’est produite.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Le format de la réponse est incorrect.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      La réponse ne contient pas de paramètre `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` n’est pas inclus dans `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Échec de récupération de la réponse dans le délai défini dans `referrerTimeout`. Augmentez la valeur et réessayez. Assurez-vous également d’avoir ouvert le lien d’acquisition avant d’installer l’application et d’utiliser le même réseau lorsque vous cliquez sur l’URL et ouvrez l’application.

À noter :

* Le serveur d’acquisition fournit une correspondance d’attribution basée sur l’adresse IP et les informations agent-utilisateur enregistrées lorsque vous cliquez sur le lien (étape 6) et lors du lancement de l’application (étape 7).

   Le réseau utilisé lorsque vous cliquez sur l’URL et lorsque vous ouvrez l’application doit être le même.

* En utilisant des outils de surveillance HTTP, les accès envoyés à partir de l’application peuvent être contrôlés pour vérifier l’attribution d’acquisition.

   Vous devriez constater qu’une demande `/v3/<appid>/start` et une demande `/v3/<appid>/end` ont été envoyées au serveur d’acquisition.

* Des variations dans l’agent-utilisateur envoyé peuvent provoquer l’échec de l’attribution.

   Assurez-vous que `https://c00.adobe.com/v3/<appid>/start` et `https://c00.adobe.com/v3/<appid>/end` ont les mêmes valeurs agent-utilisateur.

* Le lien d’acquisition et l’accès du SDK doivent utiliser le même protocole HTTP/HTTPS.

   Si le lien et l’accès utilisent des protocoles différents, où, par exemple, le lien utilise HTTP et le SDK utilise HTTPS, l’adresse IP peut différer pour certains opérateurs pour chaque demande. Cela peut provoquer l’échec de l’attribution.

* Les liens marketing sont mis en mémoire cache côté serveur et ont un délai d’expiration de 10 minutes.

   Lorsque vous modifiez des liens marketing, attendez environ 10 minutes avant de les utiliser.

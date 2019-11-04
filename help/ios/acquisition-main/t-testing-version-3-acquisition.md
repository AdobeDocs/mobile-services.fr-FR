---
description: Ces informations expliquent comment rediriger un lien de campagne d’acquisition V3 basé sur l’empreinte numérique d’un périphérique.
seo-description: Ces informations expliquent comment rediriger un lien de campagne d’acquisition V3 basé sur l’empreinte numérique d’un périphérique.
seo-title: Test de l’acquisition de V3
solution: Experience Cloud,Analytics
title: Test de l’acquisition de V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Test de l’acquisition de V3{#testing-v-acquisition}

Ces informations expliquent comment rediriger un lien de campagne d’acquisition V3 basé sur l’empreinte numérique d’un périphérique.

>[!IMPORTANT]
>
>L’acquisition V3 se rapporte aux liens d’acquisition que vous créez dans le Créateur d’acquisitions de l’interface utilisateur d’Adobe Mobile Services. Pour utiliser cette fonctionnalité, votre SDK iOS doit être mis à niveau vers la version 4.6.0 ou une version ultérieure.

Si l’application mobile n’est pas encore dans l’App Store, lorsque vous créez un lien de campagne, sélectionnez n’importe quelle application mobile en tant que destination. Seule l’application vers laquelle le serveur d’acquisition vous redirige après avoir cliqué sur le lien d’acquisition est concernée. Le lien pourra toujours être testé.

1. Effectuez les tâches préalables requises dans [Acquisition des applications mobiles](/help/ios/acquisition-main/acquisition.md).
1. Accédez au **[!UICONTROL Créateur d’acquisitions]** de l’interface utilisateur d’Adobe Mobile Services et créez une URL de campagne d’acquisition.

   Par exemple :

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Si votre lien d’acquisition se rapporte aux applications iOS et Android, utilisez l’Apple Store en tant que boutique par défaut.
1. Ouvrez le lien créé dans un navigateur de bureau et accédez à `https://c00.adobe.com/v3/<appid>/end`.

   L’élément `contextData` doit être indiqué dans la réponse JSON :

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Si `contextData` n’est pas indiqué ou si une partie de cet élément est manquante, vérifiez que l’URL d’acquisition respecte le format indiqué dans [Création manuelle d’un lien d’acquisition](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Vérifiez que les paramètres suivants du fichier de configuration sont corrects :

   | Paramètre | Valeur |
   |--- |--- |
   | acquisition | Le serveur doit être `c00.adobe.com`. *`appid`* doit être égal à l’*`appid`* de votre lien d’acquisition. |
   | analytics | La valeur de `referrerTimeout` doit être supérieure à 0. |


1. (Conditionnel) Si le paramètre `ssl` de votre fichier de configuration d’application est défini sur true, mettez votre lien d’acquisition à jour de façon à utiliser le protocole HTTPS.
1. Cliquez sur le lien créé sur le périphérique mobile sur lequel vous envisagez d’installer l’application.

   Les serveurs d’Adobe (`c00.adobe.com`) enregistrent l’empreinte numérique et vous redirigent vers l’App Store. Il n’est pas nécessaire de télécharger l’application pour effectuer les tests.
1. Lancez l’application pour la première fois à partir du même périphérique mobile que celui utilisé à l’étape 6.

   Si nécessaire, supprimez puis réinstallez l’application.
1. (Facultatif) Vous pouvez activer la journalisation du débogage du SDK pour obtenir des informations supplémentaires.

   Si tout fonctionne correctement, les journaux suivants devraient être disponibles :

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Si les journaux ci-dessus ne s’affichent pas, assurez-vous que vous avez bien effectué les étapes 4 et 5 de la procédure.

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

      Échec de récupération de la réponse dans le délai défini dans `referrerTimeout`. Augmentez la valeur et réessayez. Vérifiez également que vous avez ouvert le lien d’acquisition avant d’installer l’application et que vous utilisez le même réseau lorsque vous cliquez sur l’URL et que vous ouvrez l’application.

      À noter :

      * Le serveur d’acquisition fournit une correspondance d’attribution basée sur l’adresse IP et les informations agent-utilisateur enregistrées lorsque vous cliquez sur le lien (étape 6) et lors du lancement de l’application (étape 7).

         Le réseau utilisé lorsque vous cliquez sur l’URL et lorsque vous ouvrez l’application doit être le même.

      * En utilisant des outils de surveillance HTTP, les accès envoyés à partir de l’application peuvent être contrôlés pour vérifier l’attribution d’acquisition.

         Vous devriez constater qu’une demande `/v3/<appid>/start` et une demande `/v3/<appid>/end` ont été envoyées au serveur d’acquisition. Des variations dans l’agent-utilisateur envoyé peuvent provoquer l’échec de l’attribution.

         >[!TIP]
         >
         >Assurez-vous que `https://c00.adobe.com/v3/<appid>/start` et `https://c00.adobe.com/v3/<appid>/end` ont les mêmes valeurs agent-utilisateur.

      * Le lien d’acquisition et l’accès du SDK doivent utiliser le même protocole HTTP/HTTPS.

         En cas d’utilisation de protocoles différents (par exemple, le lien utilise HTTP et le SDK utilise HTTPS), l’adresse IP peut différer pour chaque demande (dans le cas de certains opérateurs) et l’attribution peut échouer.

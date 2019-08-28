---
description: Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.
keywords: android ; library ; mobile ; sdk
seo-description: Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.
seo-title: Test de l’acquisition héritée
solution: Marketing Cloud, Analytics
title: Test de l’acquisition héritée
topic: Développeur et mise en œuvre
uuid: bb 7 ace 96-68 eb -4 f 43-b 3 cf-af 80730 b 9 cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.

Si l’application mobile ne figure pas encore dans Google Play, vous pouvez sélectionner n’importe quelle application mobile comme destination lors de la création du lien de campagne. Une fois que vous avez cliqué sur le lien d’acquisition, seule l’application vers laquelle le serveur d’acquisition vous redirige est affectée, et non la capacité à tester le lien d’acquisition. Les paramètres de chaîne de requête sont transmis à la boutique Google Play, puis à l’application lors de l’installation dans le cadre d’une diffusion de campagne. Le test aller-retour de l’acquisition de l’application mobile requiert la simulation de ce type de diffusion.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. Ainsi, les mesures initiales de cycle de vie associées aux paramètres des chaînes de requête de la campagne sont envoyées lorsque l’application est lancée pour la première fois.

1. Dans l’interface utilisateur Adobe Mobile Services, générez une URL de campagne d’acquisition héritée.

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Connectez l’appareil à un ordinateur, lancez l’interpréteur de commandes ADB, puis l’application sur l’appareil. 
1. Envoyez une diffusion en utilisant le format suivant : 

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Procédez comme suit :
   1. Remplacez `com.example.adobetesttapp.com` par l’entrée DNS inversée de votre application.
   1. Remplacez la référence du récepteur par celle de l’emplacement du récepteur de suivi de la campagne dans l’application.
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

Si la diffusion est réussie, une réponse similaire à celle ci-dessous s’affiche :

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Vous verrez également une demande d’image envoyée aux serveurs de collecte des données d’Adobe. Si le SDK attend la durée complète de l’expiration du référent, que vous avez définie à l’étape 1, avec une demande d’image qui n’inclut pas les paramètres de campagne, la diffusion échoue.

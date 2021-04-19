---
description: Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.
keywords: android;library;mobile;sdk
seo-description: Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.
seo-title: Test de l’acquisition héritée
solution: Experience Cloud,Analytics
title: Test de l’acquisition héritée
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 100%

---

# Test de l’acquisition héritée {#testing-legacy-acquisition}

Les informations suivantes vous expliquent comment rediriger un lien de campagne d’acquisition héritée sur un appareil Android.

Si l’application mobile n’est pas encore sur Google Play, vous pouvez sélectionner n’importe quelle destination lors de la création du lien de campagne. Cela a uniquement une incidence sur l’application vers laquelle le serveur d’acquisition vous redirige lorsque vous cliquez sur le lien d’acquisition. Le lien d’acquisition pourra toujours être testé. Les paramètres de chaîne de requête sont transmis à la boutique Google Play, qui sont transmis à l’application lors de l’installation dans le cadre d’une diffusion de campagne. Les tests d’acquisition d’applications mobiles nécessitent la simulation de ce type de diffusion.

Chaque fois qu’un test est exécuté, l’application doit avoir été installée depuis peu ou ses données doivent être effacées sous **[!UICONTROL Paramètres]**. Ainsi, les mesures initiales de cycle de vie associées aux paramètres des chaînes de requête de la campagne sont envoyées lorsque l’application est lancée pour la première fois.

1. Dans l’interface utilisateur Adobe Mobile Services, générez une URL de campagne d’acquisition héritée.

   Pour plus d’informations, voir [Utilisation de liens d’acquisition hérités](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Connectez l’appareil à un ordinateur, lancez l’interpréteur de commandes ADB, puis l’application sur l’appareil.
1. Envoyez une diffusion en utilisant le format suivant :

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Procédez comme suit :
   1. Remplacez `com.example.adobetesttapp.com` par l’entrée DNS inversée de votre application.
   1. Remplacez la référence du récepteur par celle de l’emplacement du récepteur de suivi de la campagne dans l’application.
   1. Remplacez les valeurs associées à `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, etc. par les valeurs appropriées.

Si la diffusion est réussie, une réponse similaire à celle ci-dessous s’affiche :

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Une demande d’image est également envoyée aux serveurs de collecte de données d’Adobe. Si le SDK attend la durée complète du délai d’expiration du parrain que vous avez définie à l’étape 1, avec une demande d’image qui n’inclut pas les paramètres de campagne, la diffusion échoue.

---
description: Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple.
seo-description: Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple.
seo-title: Publicités Search Ads d’Apple
solution: Marketing Cloud,Analytics
title: Publicités Search Ads d’Apple
topic: Développeur et mise en œuvre
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ebcc04ab3e80aafb9d9ec2e1fbc809c743554cb7

---


# Publicités Search Ads d’Apple {#apple-search-ads}

Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple. Pour obtenir plus d’informations sur les campagnes Search Ads, voir [Apple Search Ads](https://searchads.apple.com) (en anglais).

## Avantages {#section_CEA30C652AC8470784B8054E299B80FA}

L’utilisation d’Apple Ads vous offre les avantages suivants :

* Mesurez facilement l’efficacité de vos campagnes de téléchargement d’application Search Ads en ajoutant quelques lignes de code à votre application.
* Les développeurs peuvent accéder à la date/l’heure du téléchargement et au mot-clé avec enchère ayant permis la conversion.

## Mise en œuvre des Search Ads d’Apple {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Pour mettre en oeuvre des publicités Apple, vous devez disposer du SDK iOS version 4.13.2 ou ultérieure.

Pour activer votre application pour l’attribution Search Ad, procédez comme suit :

1. Effectuez la mise en œuvre du SDK Adobe (version 4.13.2 ou ultérieure).

   Pour plus d’informations, voir [Core implementation and lifecycle](/help/ios/getting-started/dev-qs.md).

1. Ajoutez la structure iAd au fichier de projet Xcode de votre application.

## Rapport de données dans l’attribution Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Les données d’attribution Search Ads d’Apple sont fournies dans le nom, la source et les valeurs de terme de l’acquisition.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   In addition, the following values will be mapped from the `"iad"` dictionary to our typical acquisition context data fields:

   * `"iad-campaign-id"` --&gt; `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --&gt; `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --&gt; `"a.referrer.campaign.content"`
   * `"iad-keyword"` --&gt; `"a.referrer.campaign.term"`
   Ce mappage garantit que les valeurs sont disponibles dans nos rapports standard.

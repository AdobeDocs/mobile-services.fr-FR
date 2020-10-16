---
description: Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple.
seo-description: Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple.
seo-title: Publicités Search Ads d’Apple
solution: Experience Cloud,Analytics
title: Publicités Search Ads d’Apple
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---


# Publicités Search Ads d’Apple {#apple-search-ads}

Le SDK Adobe exploite les API d’attribution de l’application Search Ads d’Apple pour permettre aux développeurs et aux marketeurs de suivre et d’identifier les téléchargements d’application issus des campagnes Search Ads dans l’App Store d’Apple. Pour obtenir plus d’informations sur les campagnes Search Ads, voir [Apple Search Ads](https://searchads.apple.com/fr/).

## Avantages {#section_CEA30C652AC8470784B8054E299B80FA}

L’utilisation d’Apple Ads vous offre les avantages suivants :

* Mesurez facilement l’efficacité de vos campagnes de téléchargement d’application Search Ads en ajoutant quelques lignes de code à votre application.
* Les développeurs peuvent accéder à la date/l’heure du téléchargement et au mot-clé avec enchère ayant permis la conversion.

## Mise en œuvre des Search Ads d’Apple {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Vous devez disposer de la version 4.13.2 ou ultérieure du SDK iOS pour effectuer la mise en œuvre d’Apple Ads.

Pour activer votre application pour l’attribution Search Ads, procédez comme suit :

1. Mettez en œuvre le SDK Adobe version 4.13.2 ou ultérieure.

   Pour plus d’informations, voir [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).

1. Ajoutez la structure iAd au fichier de projet Xcode de votre application.

## Rapport de données dans l’attribution Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Les données d’attribution Search Ads d’Apple sont fournies dans le nom, la source et les valeurs de terme de l’acquisition.

   Si l’attribution = `true`, tous les champs `iad-*` seront inclus dans l’accès de cycle de vie.

   De plus, les valeurs suivantes seront mappées à partir du dictionnaire `"iad"` vers nos champs de données contextuelles de l’acquisition par défaut :

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   Ce mappage permet de s’assurer que les valeurs sont disponibles dans nos rapports de données standard.

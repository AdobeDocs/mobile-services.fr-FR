---
title: FAQ sur la fin de vie d’Adobe Mobile Services
description: Obtenez des réponses aux questions courantes concernant l’annonce de fin de vie d’Adobe Mobile Services.
source-git-commit: 0a4e0c9e6172231d8a9f9b561d0a7b7fb230473a
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 5%

---

# FAQ sur la fin de vie d’Adobe Mobile Services

La date de fin de vie d’Adobe Mobile Service est **31 décembre 2022**.

## Que se passe-t-il ?

Mobile Services arrive en fin de vie le 31 décembre 2022. Mobile Services, qui prend en charge une interface utilisateur mobile, l’acquisition, la création de liens profonds, la messagerie in-app, la notification push et la géolocalisation ne sont plus pris en charge après cette date.

## Qu’est-ce qui est inclus et qu’est-ce qui n’est pas inclus ?

Cette fin de vie comprend uniquement Adobe Mobile Services, la plateforme autonome au niveau de [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). Les SDK mobiles version 4 reposant sur cette interface ont été abandonnés le 31 août 2021.

Cette fin de vie n’inclut PAS Adobe Analytics pour les applications mobiles, qui font partie des SDK Adobe Experience Platform Mobile. Ces fonctionnalités, notamment le comportement in-app, l’analyse du cycle de vie, le suivi des interactions de messagerie et les profils d’audience, continuent de recevoir la prise en charge d’Adobe.

## Pourquoi cette fonctionnalité est-elle abandonnée ?

À mesure que Adobe continue d’étendre ses fonctionnalités de marketing mobile, les fonctionnalités précédemment disponibles dans Mobile Services seront publiées dans les solutions Adobe Experience Cloud ou proposées par le biais de Adobe Exchange Premier Partners. Cette transition vous offre des fonctionnalités de marketing mobile plus puissantes et flexibles.

## Qu’advient-il des règles de traitement existantes créées dans Mobile Services ?

[Règles de traitement](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html?lang=fr) créée ou générée dans l’interface utilisateur de Mobile Services migre automatiquement vers Adobe Analytics avant la date de fin de vie de Mobile Services. Les règles de traitement migrées se comportent de la même manière que les autres règles de traitement dans Adobe Analytics, où vous pouvez librement les afficher ou les modifier. Aucune action de l’utilisateur n’est requise pour cette migration.

Une fois que Mobile Services est mis à l’écart, toutes les logiques de règles de traitement sont traitées exclusivement dans Adobe Analytics, notamment l’utilisation de la fonction [Variables de données contextuelles](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=fr).

## Quelles sont les options de transition disponibles ?

Adobe propose trois chemins de transition en fonction du cas d’utilisation de votre entreprise.

1. **Messagerie in-app et notifications push**: Adobe peut transférer vos workflows de messagerie vers Adobe Journey Optimizer. Ce produit permet aux entreprises d’optimiser et de personnaliser les expériences sur l’ensemble du parcours client, y compris la messagerie mobile.
1. **Acquisition et liens profonds**: Les acquisitions et les liens profonds sont proposés par le biais du programme Adobe Exchange Premier Partners. L’équipe du partenariat d’Adobe peut faire des présentations appropriées pour vous assurer que vous trouvez la solution qui répond le mieux à vos besoins.
1. **Places Service**: Places Service offre des fonctionnalités de géolocalisation supplémentaires. Voir [Documentation de Places Service](https://experienceleague.adobe.com/docs/places/using/home.html?lang=fr).

## Où puis-je aller si j&#39;ai des questions ?

Voir [Page Spark de fin de vie d’Adobe Mobile Services](https://spark.adobe.com/page/C6D30y09zaRpD/) pour plus d’informations. Contactez votre représentant d’Adobe pour toute question supplémentaire.

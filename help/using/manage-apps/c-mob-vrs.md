---
description: Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.
title: Aperçu des suites de rapports
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 76%

---

# Suites de rapports virtuelles {#virtual-report-suites}

{#eol}

Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.

Les applications qui utilisent des suites de rapports virtuelles font la même chose que les applications qui ont recours à des suites de rapports standard, à l’exception de la gestion des fonctionnalités suivantes :

* Règles de traitement
* eVars/props/listvars/events
* Option Horodatage activé
* Indicateurs de Dimension (cycle de vie, emplacement, etc.)
* Classifications

Ces valeurs sont gérées dans la suite de rapports parente et partagées avec les suites de rapports virtuelles qui appartiennent à la même suite de rapports parente.

Vous pouvez accéder aux zones suivantes dans l’interface utilisateur d’Adobe Mobile Services, indépendamment de la suite de rapports parente :

* Le fichier de configuration
* Gestion des points ciblés
* Gestion des destinations de lien
* Gestion des postbacks
* Liens des messages
* Acquisition

Une suite de rapports virtuelle peut vous aider à terminer les tâches suivantes :

* Limitation de l’accès aux données

   Une société multinationale possède une application qui envoie des données à une suite de rapports pour tous les emplacements géographiques. Cependant, l’administrateur de la société souhaite empêcher l’utilisateur professionnel d’une région de voir les données d’une autre région. L’administrateur de la société peut créer une suite de rapports virtuelle pour segmenter les utilisateurs par région et donner une autorisation d’accès à la suite uniquement à l’utilisateur professionnel qui gère la région.

   Cette restriction empêche les utilisateurs professionnels de voir les données qui ne sont pas liées à leur région. Par exemple, un utilisateur professionnel situé en région EMEA n’a nullement besoin de connaître les données de la région APAC.

* Autorisation de contrôle de la messagerie push/in-app, des points ciblés d’emplacement, de l’acquisition et de postbacks, toutes les données étant envoyées vers une seule suite de rapports.

   Une entreprise multinationale souhaite que toutes ses données soient envoyées vers la même suite de rapports pour les emplacements géographiques. Cependant, elle souhaite que l’équipe marketing de chaque région gère ses propres messages push/in-app. L’administrateur de la société peut créer des suites de rapports virtuelles régionales et chaque équipe peut gérer leur propre application, en fonction de cette suite.

   L’équipe régionale crée une application en utilisant le fichier de configuration issu de la suite de rapports virtuelle. Les données sont envoyées à la suite de rapports parente, mais les messages push/in-app, les points ciblés d’emplacement et les postbacks sont contrôlés dans l’application qui a été créée à partir de la suite de rapports virtuelle.

## Création d’une suite de rapports virtuelle dans Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Seuls les administrateurs Adobe Analytics peuvent créer et modifier des suites de rapports virtuelles dans Adobe Analytics. Pour créer une suite de rapports virtuelle, voir [Création de suites de rapports virtuelles](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html?lang=fr) dans la documentation Adobe Analytics.

Chaque suite de rapports virtuelle possède un ID unique. Pour afficher l’identifiant de la suite de rapports parente dans l’interface utilisateur d’Adobe Mobile Services, sur la page Gestion des paramètres de l’application, dans la section **[!UICONTROL Informations sur l’application]**, cliquez sur **[!UICONTROL Plus de détails]**.

Dans l’interface utilisateur d’Adobe Mobile Services, vous pouvez utiliser une suite de rapports virtuelle pour créer une application et segmenter les données vers un groupe spécifique de votre entreprise. Ainsi, par exemple, un utilisateur chargé de la conception d’entreprise en Espagne ne peut pas consulter les données pertinentes pour un utilisateur chargé de la conception d’entreprise au Japon.

>[!TIP]
>
>Vous ne pouvez pas modifier les valeurs qui sont héritées de la suite de rapports parente.

Une suite de rapports virtuelle est une définition de segment côté serveur qui est jointe à une suite de rapports parente. Par conséquent, vous ne pouvez pas effectuer de collecte de données vers une suite de rapports virtuelle, car le SDK envoie les accès uniquement à la suite de rapports parente, qui à son tour enregistre les accès.

## Suite de rapports virtuelle dans Adobe Mobile Services et collecte de données {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Dans Adobe Mobile Services, vous pouvez créer une application basée sur une suite de rapports parente ou une suite de rapports virtuelle. Lors de la création d’une application basée sur une suite de rapports virtuelle, nous recommandons d’aligner le segment de la suite virtuelle avec la définition de l’application.

>[!TIP]
>
>Les certifications push sont jointes au niveau de l’application dans l’interface utilisateur de Mobile Services.

Afin de garantir l’envoi de vos messages push, le segment d’audience doit être correctement défini. Pour plus d’informations, voir [Audience : Définition et configuration des segments d’audience pour les messages push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Comprendre les fuseaux horaires {#section_498E1EED22D741C3BDED44F01FACA72A}

La propriété de fuseaux horaires de la page Gestion des paramètres de l’application est différente de celle qui est utilisée pour créer une suite de rapports virtuelle dans Adobe Analytics. La propriété de la page Gérer les paramètres de l’application est héritée de la suite de rapports parente qui est utilisée pour envoyer les données à Adobe Analytics. La propriété que vous spécifiez à la création de la suite virtuelle dans Adobe Analytics est utilisée pour afficher les rapports dans l’interface utilisateur de Mobile Services et peut être différente de celle de la suite parente.

## Sélection d’une suite de rapports virtuelle dans l’interface utilisateur de Mobile Services {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Pour utiliser une suite de rapports virtuelle, sélectionnez-la, à la création de l’application, dans la liste déroulante **[!UICONTROL Suite de rapports]** sur la page Informations de l’application. Cette liste contient des suites de rapports parentes et virtuelles.

>[!IMPORTANT]
>
>Pour sélectionner une suite de rapports virtuelle dans la liste, repérez l’option avec le point bleu et la convention d’appellation `vrs_` *`<company_name>`*`_`*`<unique name>`*  .

## Propriétés de la suite de rapports virtuelle {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Voici les propriétés des suites de rapports virtuelles :

>[!TIP]
>
>Les propriétés en lecture seule sont héritées de la suite de rapports parente.

| Propriété | Hérité de la suite de rapports parente | Modifiable? | Notes |
|--- |--- |--- |--- |
| `target.clientCode` | Non | Oui |  |
| `target.timeout` | Non | Oui |  |
| `audienceManager.server` | Non | Oui |  |
| `audienceManager.analyticsForwardingEnabled` | Oui | Oui |  |
| `audienceManager.timeout` | Non | Oui |  |
| `acquisition.server` | Non | Non |  |
| `acquisition.appid` | Non | Non |  |
| `analytics.rsids` | Oui | Non |  |
| `analytics.server` | Non | Non |  |
| `analytics.ssl` | Non | Oui |  |
| `analytics.offlineEnabled` | Oui |  |  |
| `analytics.charset` | Oui | Non |  |
| `analytics.lifecycleTimeout` | Non | Oui | Doit être la suite de rapports parente, si les utilisateurs ne souhaitent pas que leurs données soient incohérentes. |
| `analytics.privacyDefault` | Non | Oui |  |
| `analytics.batchLimit` | Non | Oui |  |
| `analytics.timezone` | Oui | Oui, lorsque vous créez l’application pour la première fois. | Cette propriété de fuseau horaire est utilisée pour envoyer des données à Adobe Analytics et est différente de la propriété de fuseau horaire définie lors de la création d’une suite de rapports virtuelle. |
| `analytics.timezoneOffset` | Oui | Non |  |
| `analytics.referrerTimeout` | Non | Oui |  |
| `analytics.backdateSessionInfo` | Oui | Oui |  |

## Informations supplémentaires  {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Voici quelques informations supplémentaires sur les suites de rapports virtuelles :

* Pour plus d’informations sur les suites de rapports virtuelles, voir [Suites de rapports virtuelles - Aperçu](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=fr).
* Pour plus d’informations sur l’organisation de la mise en œuvre d’une suite de rapports virtuelle, voir [Processus de mise en œuvre des suites de rapports virtuelles](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).

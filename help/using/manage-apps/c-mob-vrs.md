---
description: Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.
seo-description: Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.
seo-title: Aperçu des suites de rapports
title: Aperçu des suites de rapports
uuid: 3 f 467 cad -43 e 7-4 cd 0-889 b -89 f 8 c 61 febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Ainsi, les utilisateurs peuvent conserver leurs données dans une suite de rapports, mais gérer les données comme s'il était dans des suites de rapports distinctes.

Les applications qui utilisent les suites de rapports virtuelles font la même chose que les applications qui utilisent une suite de rapports standard, à l'exception de la gestion des fonctionnalités suivantes :

* Règles de traitement
* eVar/prop/listVar/événement
* Option Horodatage
* Drapeaux de dimension (cycle de vie, emplacement, etc.)
* Classifications

Ces valeurs sont gérées dans la suite de rapports parente et partagées avec les suites de rapports virtuelles qui appartiennent à la même suite parente.

Vous pouvez accéder aux zones suivantes dans l'interface utilisateur d'Adobe Mobile Services indépendamment de la suite de rapports parente :

* Fichier de configuration
* Gestion des points ciblés
* Gestion des destinations de lien
* Gestion des postbacks
* Liens des messages
* Acquisition

Une suite de rapports virtuelle peut vous aider à accomplir les tâches suivantes :

* Restriction de l’accès aux données

   Une entreprise multinationale possède une application qui envoie des données à une suite de rapports pour tous emplacements géographiques. Cependant, l’administrateur de la société souhaite empêcher l’utilisateur professionnel d’une région de voir les données d’une autre région. L'administrateur de l'entreprise peut créer une suite de rapports virtuelle pour segmenter les utilisateurs par région et accorder l'autorisation à la suite de rapports virtuelle uniquement à l'utilisateur professionnel qui gère la région.

   Cette restriction empêche les utilisateurs professionnels de voir les données qui ne sont pas liées à leur région. Par exemple, un utilisateur professionnel situé en région EMEA n’a nullement besoin de connaître les données de la région APAC.

* Permet de contrôler la messagerie in-app/push, les POI d'emplacement, l'acquisition et les postbacks avec toutes les données envoyées à une suite de rapports.

   Une entreprise multinationale souhaite que toutes ses données soient envoyées vers la même suite de rapports pour les emplacements géographiques. Cependant, elle souhaite que l’équipe marketing de chaque région gère ses propres messages push/in-app. L’administrateur de la société peut créer des suites de rapports virtuelles régionales et chaque équipe peut gérer leur propre application, en fonction de cette suite.

   L’équipe régionale crée une application en utilisant le fichier de configuration issu de la suite de rapports virtuelle. Les données sont envoyées à la suite de rapports parente, mais la messagerie in-app/push, les POI d'emplacement, l'acquisition et les postbacks sont contrôlés dans l'application créée à partir de la suite de rapports virtuelle.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Seuls les administrateurs d'Adobe Analytics peuvent créer et modifier des suites de rapports virtuelles dans Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Chaque suite de rapports virtuelle possède un identifiant unique. Pour afficher l'ID de suite de rapports parente dans l'interface utilisateur d'Adobe Mobile Services, dans la page Gérer les paramètres de l'application, **[!UICONTROL cliquez sur]** **[!UICONTROL Plus de détails dans la section Informations de l'application]**.

Dans l’interface utilisateur d’Adobe Mobile Services, vous pouvez créer une application et des données de segment pour un groupe spécifique dans votre entreprise. De cette manière, un utilisateur professionnel espagnol ne peut pas, par exemple, voir les données qui concernent un utilisateur professionnel japonais.

>[!TIP]
>
>Vous ne pouvez pas modifier les valeurs héritées de la suite de rapports parente.

Une suite de rapports virtuelle est une définition de segment côté serveur, elle est liée à une suite de rapports parente. En conséquence, vous ne pouvez effectuer une collecte de données vers une suite virtuelle, car le SDK envoie des accès à la suite parente uniquement, qui enregistre ensuite les accès.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Dans Adobe Mobile Services, vous pouvez créer une application basée sur une suite de rapports parente ou une suite de rapports virtuelle. Lors de la création d’une application basée sur une suite de rapports virtuelle, nous recommandons d’aligner le segment de la suite virtuelle avec la définition de l’application.

>[!TIP]
>
>Les certifications Push sont jointes au niveau de l'application dans l'interface utilisateur des services mobiles.

Afin de garantir l’envoi de vos messages push, le segment d’audience doit être correctement défini. Pour plus d'informations, voir [Audience : Définition et configuration des segments d'audience pour les messages Push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

La propriété Fuseau horaire de la page Gérer les paramètres de l'application est différente de la propriété Fuseau horaire que vous utilisez pour créer la suite de rapports virtuelle dans Adobe Analytics. La propriété de la page Gérer les paramètres de l’application est héritée de la suite de rapports parente qui est utilisée pour envoyer les données à Adobe Analytics. La propriété que vous spécifiez lors de la création de la suite de rapports virtuelle dans Adobe Analytics est utilisée pour afficher les rapports dans l'interface utilisateur des services mobiles et peut être différente de la suite de rapports parente.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Pour utiliser une suite de rapports virtuelle, sélectionnez-la, à la création de l’application, dans la liste déroulante **[!UICONTROL Suite de rapports]** sur la page Informations de l’application. Cette liste contient des suites de rapports parentes et virtuelles.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Voici les propriétés des suites de rapports virtuelles :

>[!TIP]
>
>Les propriétés en lecture seule sont héritées de la suite de rapports parente.

| Propriété | Héritée de la suite de rapports parente | Modifiable ? | Remarques |
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
| `analytics.lifecycleTimeout` | Non | Oui | Devrait être la suite de rapports parente, si les utilisateurs ne souhaitent pas que leurs données soient incohérentes. |
| `analytics.privacyDefault` | Non | Oui |  |
| `analytics.batchLimit` | Non | Oui |  |
| `analytics.timezone` | Oui | Oui, si vous créez l’application en premier. | Cette propriété de fuseaux horaires est utilisée pour envoyer des données à Adobe Analytics et est différente de la propriété de fuseaux horaires qui est définie à la création d’une suite de rapports virtuelle. |
| `analytics.timezoneOffset` | Oui | Non |  |
| `analytics.referrerTimeout` | Non | Oui |  |
| `analytics.backdateSessionInfo` | Oui | Oui |  |

## Informations supplémentaires {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Voici quelques informations supplémentaires sur les suites de rapports virtuelles :

* Pour plus d’informations sur les suites de rapports virtuelles, voir [Suites de rapports virtuelles](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).
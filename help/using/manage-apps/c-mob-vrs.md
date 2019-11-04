---
description: Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.
seo-description: Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.
seo-title: Aperçu des suites de rapports
title: Aperçu des suites de rapports
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: ht
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Suites de rapports virtuelles{#virtual-report-suites}

Une suite de rapports virtuelle (VRS) est une suite de rapports créée en appliquant une ou plusieurs définitions de segmentation à une suite de rapports. Grâce à cette fonctionnalité, les utilisateurs peuvent conserver leurs données dans une suite de rapports unique, et les gérer comme si elles se trouvaient dans des suites de rapports distinctes.

Les applications qui utilisent des suites de rapports virtuelles font la même chose que les applications qui ont recours à des suites de rapports standard, à l’exception de la gestion des fonctionnalités suivantes :

* Règles de traitement
* eVar/prop/listVar/événement
* Option Horodatage activé
* Drapeaux de dimension (cycle de vie, emplacement, etc.)
* Classifications

Ces valeurs sont gérées dans la suite de rapports parente et partagées avec les suites de rapports virtuelles qui appartiennent à la même suite parente.

Vous pouvez accéder aux zones suivantes dans l’interface utilisateur d’Adobe Mobile Services, indépendamment de la suite de rapports parente :

* Fichier de configuration
* Gestion des points ciblés
* Gestion des destinations de lien
* Gestion des postbacks
* Liens des messages
* Acquisition

Une suite de rapports virtuelle peut vous aider à terminer les tâches suivantes :

* Restriction de l’accès aux données

   Une entreprise multinationale possède une application qui envoie des données à une suite de rapports pour tous emplacements géographiques. Cependant, l’administrateur de la société souhaite empêcher l’utilisateur professionnel d’une région de voir les données d’une autre région. L’administrateur de la société peut créer une suite de rapports virtuelle pour segmenter les utilisateurs par région et donner une autorisation d’accès à la suite uniquement à l’utilisateur professionnel qui gère la région.

   Cette restriction empêche les utilisateurs professionnels de voir les données qui ne sont pas liées à leur région. Par exemple, un utilisateur professionnel situé en région EMEA n’a nullement besoin de connaître les données de la région APAC.

* Autorisation de contrôle de la messagerie push/in-app, des points ciblés d’emplacement, de l’acquisition et de postbacks, toutes les données étant envoyées vers une seule suite de rapports.

   Une entreprise multinationale souhaite que toutes ses données soient envoyées vers la même suite de rapports pour les emplacements géographiques. Cependant, elle souhaite que l’équipe marketing de chaque région gère ses propres messages push/in-app. L’administrateur de la société peut créer des suites de rapports virtuelles régionales et chaque équipe peut gérer leur propre application, en fonction de cette suite.

   L’équipe régionale crée une application en utilisant le fichier de configuration issu de la suite de rapports virtuelle. Les données sont envoyées à la suite de rapports parente, mais les messages push/in-app, les points ciblés d’emplacement et les postbacks sont contrôlés dans l’application qui a été créée à partir de la suite de rapports virtuelle.

## Création d’une suite de rapports virtuelle dans Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Seuls les administrateurs Adobe Analytics peuvent créer et modifier des suites de rapports virtuelles dans Adobe Analytics. Pour créer une suite de rapports virtuelle, voir [Création de suites de rapports virtuelles](https://docs.adobe.com/content/help/fr-FR/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Chaque suite de rapports virtuelle possède un identifiant unique. Pour afficher l’identifiant de la suite de rapports parente dans l’interface utilisateur d’Adobe Mobile Services, sur la page Gestion des paramètres de l’application, dans la section **[!UICONTROL Informations sur l’application]**, cliquez sur **[!UICONTROL Plus de détails]**.

Dans l’interface utilisateur d’Adobe Mobile Services, vous pouvez créer une application et des données de segment pour un groupe spécifique dans votre entreprise. De cette manière, un utilisateur professionnel espagnol ne peut pas, par exemple, voir les données qui concernent un utilisateur professionnel japonais.

>[!TIP]
>
>Vous ne pouvez pas modifier les valeurs qui sont héritées de la suite de rapports parente.

Une suite de rapports virtuelle est une définition de segment côté serveur, elle est liée à une suite de rapports parente. En conséquence, vous ne pouvez effectuer une collecte de données vers une suite virtuelle, car le SDK envoie des accès à la suite parente uniquement, qui enregistre ensuite les accès.

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
>Pour sélectionner une suite de rapports virtuelle dans la liste, repérez l’option avec le point bleu et la convention d’appellation `vrs_` *`<company_name>`* `_` *`<unique name>`*.

## Propriétés de la suite de rapports virtuelle {#section_20ECE6243F664C4FB4347ADB4FF0458A}

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

Voici quelques informations supplémentaires sur les suites de rapports virtuelles :

* Pour plus d’informations sur les suites de rapports virtuelles, voir [Suites de rapports virtuelles](https://docs.adobe.com/content/help/fr-FR/analytics/components/virtual-report-suites/vrs-about.html).
* Pour plus d’informations sur l’organisation de la mise en œuvre d’une suite de rapports virtuelle, voir [Processus de mise en œuvre des suites de rapports virtuelles](https://docs.adobe.com/content/help/fr-FR/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).
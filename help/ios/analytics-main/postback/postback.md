---
description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-title: Postbacks
solution: Marketing Cloud,Analytics
title: Présentation des postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Présentation des postbacks {#postbacks}

Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Cette fonctionnalité nécessite le SDK version 4.6.0 ou ultérieure.

Les messages postback sont placés en file d’attente et suivent toutes les règles en ligne/hors ligne existantes qui régissent la collecte des données d’analyse. Lorsqu’un message correspond (comme c’est le cas des messages affichés), les messages postback n’annulent pas le reste des messages. Cela permet à plusieurs postbacks de se produire sur le même accès Analytics. Pour consulter une définition, voir la ligne *postbacks* dans la section [Fichier de configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. Les valeurs disponibles pour l’extension de modèle sont limitées à celles de la [liste des variables du cycle de vie standard](/help/ios/metrics.md), plus toute autre donnée personnalisée annexée à l’accès qui déclenche le message. Aucune donnée historique ou donnée basée sur des segments n’est disponible à ce stade.

Il existe également des modèles spécifiques et réservés que le SDK va automatiquement remplacer par les données internes connues du SDK.

Cette liste comprend ce qui suit :

| Nom du jeton | Description du jeton |
|--- |--- |
| `{%sdkver%}` | Renvoie la version du SDK. |
| `{%cachebust%}` | Résout un nombre aléatoire entre 1 et 100 000 000. |
| `{%adid%}` | Renvoie l’identifiant IDFA. Ce jeton ne fonctionne que si vous l’avez utilisé `setAdvertisingIdentifier`. |
| `{%pushid%}` | Renvoie le jeton d’identifiant Push. Ce jeton ne fonctionne que si vous l’avez utilisé `setPushIdentifier`. |
| `{%timestampu%}` | Renvoie l’horodatage actuel en heure époque. |
| `{%timestampz%}` | Renvoie l’horodatage actuel au format JavaScript (ISO 8601). |
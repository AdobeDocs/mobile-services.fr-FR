---
description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Présentation des postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: ht
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Présentation des postbacks {#postbacks}

Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.6.0 ou ultérieure du SDK

Les messages postback sont placés en file d’attente et suivent toutes les règles en ligne/hors ligne existantes qui régissent la collecte des données d’analyse. Lorsqu’un message correspond (comme c’est le cas des messages affichés), les messages postback n’annulent pas le reste des messages. Cela permet à plusieurs postbacks de se produire sur le même accès Analytics. Pour consulter une définition, voir la ligne *postbacks* dans la section [Fichier de configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Extensions de modèles {#section_6758AD05A24C4E9E965F5253294C164A}

Les extensions de modèles sont disponibles dans les propriétés `templateurl` et `templatebody`. Les éléments du modèle prennent le format `{key}`, où `key` est une clé de données contextuelles ou de données standard. Les valeurs disponibles pour l’extension de modèle sont limitées à celles de la [liste des variables du cycle de vie standard](/help/ios/metrics.md), plus toute autre donnée personnalisée annexée à l’accès qui déclenche le message. Aucune donnée historique ou donnée basée sur des segments n’est disponible à ce stade.

Il existe également des modèles spécifiques et réservés que le SDK va automatiquement remplacer par les données internes connues du SDK.

Cette liste comprend ce qui suit :

| Nom du jeton | Description du jeton |
|--- |--- |
| `{%sdkver%}` | Renvoie la version du SDK. |
| `{%cachebust%}` | Résout un nombre aléatoire entre 1 et 100 000 000. |
| `{%adid%}` | Renvoie l’identifiant IDFA. Ce jeton ne fonctionne que si vous avez utilisé `setAdvertisingIdentifier`. |
| `{%pushid%}` | Renvoie le jeton d’identifiant Push. Ce jeton ne fonctionne que si vous avez utilisé `setPushIdentifier`. |
| `{%timestampu%}` | Renvoie l’horodatage actuel en heure époque. |
| `{%timestampz%}` | Renvoie l’horodatage actuel au format JavaScript (ISO 8601). |
---
description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
keywords: android;library;mobile;sdk
seo-description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Présentation des postbacks
topic: Développeur et mise en œuvre
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.6.0 ou ultérieure du SDK

Les messages postback sont placés en file d’attente et suivent toutes les règles en ligne/hors ligne existantes qui régissent la collecte des données d’analyse. Lorsqu’un message correspond (comme c’est le cas des messages affichés), les messages postback n’annulent pas le reste des messages. Cela permet à plusieurs postbacks de se produire sur le même accès Analytics. Pour consulter une définition, voir la ligne *postbacks* dans la section [Fichier de configuration JSON ADBMobile](/help/android/configuration/json-config/json-config.md).

## Extensions de modèles {#section_6758AD05A24C4E9E965F5253294C164A}

Les extensions de modèle sont disponibles dans les propriétés `templateurl` et `templatebody`. Les éléments du modèle prennent le format `{key}`, où `key` est une clé de données contextuelles ou de données standard. Les valeurs disponibles pour l’extension de modèle sont limitées à la [liste des mesures du cycle de vie](/help/android/metrics.md), en plus des données personnalisées jointes à l’accès qui déclenche le message. Aucune donnée d’historique ou de segment n’est disponible à l’heure actuelle.

Il existe également des modèles spécifiques réservés que le SDK remplace automatiquement par des données internes connues du SDK.

Cette liste inclut :

| Nom du jeton | Description du jeton |
|--- |--- |
| {%sdkver%} | Renvoie la version du SDK. |
| {%cachebust%} | Résout un nombre aléatoire entre 1 et 100 000 000. |
| {%adid%} | Renvoie l’identifiant publicitaire pour Android. Remarque : Ce jeton fonctionne uniquement si vous avez utilisé `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Renvoie le jeton d’identifiant Push. Remarque : Ce jeton fonctionne uniquement si vous avez utilisé `setPushIdentifier`. |
| {%timestampu%} | Renvoie l’horodatage actuel en heure époque. |
| {%timestampz%} | Renvoie l’horodatage actuel au format JavaScript (ISO 8601). |
---
description: Les postbacks permettent d’envoyer des données collectées par le SDK à un serveur tiers. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
keywords: android;library;mobile;sdk
seo-description: Les postbacks permettent d’envoyer des données collectées par le SDK à un serveur tiers. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Présentation des postbacks
topic: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 38%

---


# Postbacks {#postbacks}

Les postbacks permettent d’envoyer des données collectées par le SDK à un serveur tiers. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.6.0 ou ultérieure du SDK

Les messages postback sont placés en file d’attente et suivent toutes les règles en ligne/hors ligne qui régissent la collecte de données d’analyse. Lorsqu’un message correspond (comme le font les messages affichés), les messages postback n’annulent pas le reste des messages. Cela permet plusieurs postbacks sur le même accès Analytics. Pour consulter une définition, voir la ligne *postbacks* dans la section [Fichier de configuration JSON ADBMobile](/help/android/configuration/json-config/json-config.md).

## Extensions de modèles {#section_6758AD05A24C4E9E965F5253294C164A}

Les extensions de modèle sont disponibles dans les propriétés `templateurl` et `templatebody`. Les éléments du modèle prennent le format `{key}`, où `key` est une clé de données contextuelles ou de données standard. Les valeurs disponibles pour l’extension de modèle sont limitées à la [liste des mesures du cycle de vie](/help/android/metrics.md), en plus des données personnalisées jointes à l’accès qui déclenche le message. Aucune donnée basée sur l’historique ou les segments n’est disponible pour le moment.

Il existe également des modèles réservés spécifiques que le SDK remplacera automatiquement par des données internes connues du SDK.

Cette liste comprend :

| Nom du jeton | Description du jeton |
|--- |--- |
| {%sdkver%} | Renvoie la version du SDK. |
| {%cachebust%} | Résout un nombre aléatoire entre 1 et 100 000 000. |
| {%adid%} | Renvoie l’identifiant publicitaire pour Android. Remarque : Ce jeton fonctionne uniquement si vous avez utilisé `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Renvoie le jeton d’identifiant Push. Remarque : Ce jeton fonctionne uniquement si vous avez utilisé `setPushIdentifier`. |
| {%timestampu%} | Renvoie l’horodatage actuel en heure époque. |
| {%timestampz%} | Renvoie l’horodatage actuel au format JavaScript (ISO 8601). |
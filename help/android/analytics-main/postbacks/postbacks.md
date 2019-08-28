---
description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
keywords: android ; library ; mobile ; sdk
seo-description: Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.
seo-title: Postbacks
solution: Marketing Cloud, Analytics
title: Présentation des postbacks
topic: Développeur et mise en œuvre
uuid: 8 bfd 4374-2767-421 d -891 d-e 1 e 9 a 99 b 6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Les postbacks permettent d’envoyer vers un serveur tiers des données collectées par le SDK. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer le SDK pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Cette fonctionnalité requiert le SDK version 4.6.0 ou ultérieure.

Les messages postback sont placés en file d’attente et suivent toutes les règles en ligne/hors ligne existantes qui régissent la collecte des données d’analyse. Lorsqu’un message correspond (comme c’est le cas des messages affichés), les messages postback n’annulent pas le reste des messages. Cela permet à plusieurs postbacks de se produire sur le même accès Analytics. Pour consulter une définition, voir la ligne *postbacks* dans la section [Fichier de configuration JSON ADBMobile](/help/android/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. Aucune donnée d’historique ou de segment n’est disponible à l’heure actuelle.

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
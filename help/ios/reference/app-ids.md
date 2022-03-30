---
description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et Adobe Mobile Services.
solution: Experience Cloud Services,Analytics
title: ID d’application
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# ID d’application {#app-ids}

Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et Adobe Mobile Services.

| Identifiant | Description |
|--- |--- |
| Identifiant envoyé avec les mesures de cycle de vie | Il s’agit d’une combinaison du nom de l’application et de la version du lot qui est soumise à la boutique d’applications.  Cette valeur est utilisée pour le rapport de versions dans Adobe Mobile Services. Vous pouvez l’utiliser pour filtrer les résultats en fonction d’une version spécifique de votre application. |
| ID de la boutique d’applications | Cet ID est affecté à l’application par la boutique d’applications et est fourni par Adobe Mobile Services lorsque vous créez des liens d’acquisition. |
| AppID dans le fichier de configuration JSON ADBMobile | Cet ID unique est attribué par Adobe Mobile Services à l’instance d’application pour toutes les métadonnées associées dans votre système.  Cet identifiant est utilisé pour créer des URL uniques pour le lien de suivi d’acquisition ou de suivi ; il est automatiquement ajouté au fichier de configuration ADBMobile JSON lorsqu’il est téléchargé à partir de l’interface utilisateur. Vous pouvez le retrouver sous Gérer les paramètres d’application, dans les paramètres Acquisition de votre application. |

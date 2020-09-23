---
description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et les services Adobe Mobile.
seo-description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et les services Adobe Mobile.
seo-title: ID d’application
solution: Experience Cloud,Analytics
title: ID d’application
topic: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 61%

---


# ID d’application {#app-ids}

Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et les services Adobe Mobile.

| Identifiant | Description |
|--- |--- |
| ID envoyé avec les mesures de cycle de vie | Il s’agit d’une combinaison du nom de l’application et de la version du lot qui est soumise à la boutique d’applications.  Cette valeur est utilisée pour le rapport de versions dans Adobe Mobile Services. Vous pouvez l’utiliser pour filtrer les résultats en fonction d’une version spécifique de votre application. |
| ID de la boutique d’applications | Cet identifiant est attribué à votre application par la boutique d’applications et est fourni dans les services mobiles d’Adobe lorsque vous créez des liens d’acquisition. |
| AppID dans le fichier de configuration JSON ADBMobile | Cet identifiant unique est attribué par Adobe Mobile Services à l’instance d’application pour toutes les métadonnées associées dans votre système.  Cet identifiant est utilisé pour créer des URL uniques pour le lien de suivi d’acquisition ou de suivi ; il est automatiquement ajouté au fichier de configuration ADBMobile JSON lorsqu’il est téléchargé à partir de l’interface utilisateur. Vous pouvez le retrouver sous Gérer les paramètres d’application, dans les paramètres Acquisition de votre application. |


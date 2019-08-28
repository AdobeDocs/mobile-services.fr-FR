---
description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et Adobe Mobile Services.
seo-description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et Adobe Mobile Services.
seo-title: ID d’application
solution: Marketing Cloud, Analytics
title: ID d’application
topic: Développeur et mise en œuvre
uuid: 24 ebc 716-23 c 7-4 ee 8-8256-b 534210367 e 0
translation-type: tm+mt
source-git-commit: 0e22d5e080b680ff6b23462f1bc12f27d99e6d42

---


# ID d’application {#app-ids}

Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK iOS et Adobe Mobile Services.

| ID | Description |
|--- |--- |
| ID envoyé avec les mesures de cycle de vie | Il s’agit d’une combinaison du nom de l’application et de la version du lot qui est soumise à la boutique d’applications.  Cette valeur est utilisée pour le rapport de versions dans Adobe Mobile Services. Vous pouvez l’utiliser pour filtrer les résultats en fonction d’une version spécifique de votre application. |
| ID de la boutique d’applications | Cet ID est affecté à l’application par la boutique d’applications et est fourni par Adobe Mobile Services lorsque vous créez des liens d’acquisition. |
| AppID dans le fichier de configuration JSON ADBMobile | Cet identifiant unique est attribué par Adobe Mobile Services à l’instance d’application pour toutes les métadonnées associées dans votre système.  Cet identifiant est utilisé pour créer des URL uniques pour le lien de suivi d’acquisition ou de suivi ; il est automatiquement ajouté au fichier de configuration ADBMobile JSON lorsqu’il est téléchargé à partir de l’interface utilisateur. Vous pouvez le retrouver sous Gérer les paramètres d’application, dans les paramètres Acquisition de votre application. |

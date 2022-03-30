---
description: Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK Android et Adobe Mobile Services.
solution: Experience Cloud Services,Analytics
title: ID d’application
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# ID d’application{#app-ids}

Le tableau suivant décrit les différents identifiants d’application utilisés par le SDK Android et Adobe Mobile Services.

| Identifiant | Description |
|--- |--- |
| Identifiant envoyé avec les mesures de cycle de vie | Il s’agit d’une combinaison du nom de l’application et de la version du lot qui est soumise à la boutique d’applications. Cette valeur est utilisée pour le rapport Versions d’Adobe Mobile Services ; vous pouvez l’utiliser comme filtre pour segmenter les données du rapport par versions spécifiques de l’application. |
| ID de la boutique d’applications | Cet ID est affecté à l’application par la boutique d’applications et est fourni par Adobe Mobile Services lorsque vous créez des liens d’acquisition. |
| AppID dans le fichier de configuration JSON ADBMobile | Cet ID unique est attribué par Adobe Mobile Services à l’instance d’application pour toutes les métadonnées associées dans votre système. Cet identifiant est utilisé pour créer les URL uniques pour le suivi des acquisitions ou des liens. Cet identifiant est automatiquement ajouté au fichier de configuration JSON ADBMobile lors de son téléchargement depuis l’interface utilisateur. Il se trouve dans Gérer les paramètres d’application sous les paramètres Acquisition de l’application. |

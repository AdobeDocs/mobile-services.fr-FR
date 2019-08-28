---
description: Le rapport Chemins d’accès des vues est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées entre deux états de l’application.
keywords: mobile
seo-description: Le rapport Chemins d’accès des vues est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées entre deux états de l’application.
seo-title: Rapport Chemins d'accès
solution: Marketing Cloud, Analytics
title: Rapport Chemins d'accès
topic: Rapports, Mesures
uuid: bc 73 edce -0 cc 0-4349-9 a 48-e 0 a 40 cbe 1 b 67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Rapport Chemins d'accès {#view-paths}

Le rapport **[!UICONTROL Chemins d’accès des vues]est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées entre deux états de l’application.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. Le rapport **[!UICONTROL Chemins d’accès des vues]vous permet de visualiser la manière dont les utilisateurs naviguent d’un écran à l’autre au sein de votre application.** Le rapport **[!UICONTROL Chemins d’accès des actions]montre la séquence des actions (événements tels que des clics, sélections, redimensionnements, etc.) accomplies par les utilisateurs dans votre application.** Vous pouvez utiliser un rapport Entonnoir pour combiner la navigation et les actions dans un rapport. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![afficher les chemins](assets/view_paths.png)

Chaque nœud matérialisé par une case représente un état dans les chemins d’accès empruntés par les utilisateurs dans une application. À titre d’exemple, sur l’illustration ci-dessus, le nœud supérieur représente le nombre d’utilisateurs qui ont lancé l’application, puis ont navigué vers la vue principale.

Lorsque vous cliquez sur un nœud pour afficher les options supplémentaires de modification du graphique, des options telles que **[!UICONTROL Mise au point]** ou **Développer]apparaissent.[!UICONTROL ** Si, par exemple, vous cliquez sur l’état **[!UICONTROL MainView]** dans le nœud supérieur, les icônes **[!UICONTROL Mise au point]et** Développer] s’affichent.**[!UICONTROL **

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. Sur l’illustration ci-dessous, l’état 1 lance l’application, l’état 2 visualise la page principale de l’application et l’état 3 inclut les chemins d’accès suivants empruntés par les utilisateurs :

* Navigation vers la pellicule
* Navigation vers le sélecteur d’éléments
* Navigation vers l’appareil photo
* Navigation vers la page d’informations sur l’élément

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. Sur l’illustration ci-dessous, les chemins d’accès suivants ont été empruntés avant que les utilisateurs ne visualisent la vue principale de l’application :

* Informations sur l’élément
* Sélecteur d’éléments
* Pellicule
* Appareil photo

![focus du chemin d'accès](assets/view_paths_focus.png)

Vous pouvez effectuer une mise au point ou développer plusieurs nœuds afin d’obtenir une vue détaillée des chemins d’accès empruntés par les utilisateurs dans votre application. Par exemple :

![chemin d'affichage multi-chemin](assets/view_paths_mult.png)

Vous pouvez configurer les options suivantes pour ce rapport :

* **[!UICONTROL Période de la période]** Cliquez sur l'icône **[!UICONTROL Calendrier]** pour sélectionner une période personnalisée ou pour sélectionner une période prédéfinie dans la liste déroulante.
* **[!UICONTROL Personnalisez]**
les rapports en modifiant les options **[!UICONTROL Afficher par]** , en ajoutant des mesures et des filtres et en ajoutant des séries supplémentaires (mesures), etc. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filtre Filtre]**
 **[!UICONTROL de clics]** pour créer un filtre couvrant différents rapports afin de visualiser les performances d'un segment dans tous les rapports mobiles. Un filtre d’attractivité vous permet de définir un filtre qui est appliqué à tous les rapports autres que de cheminement. Pour plus d'informations, voir [Ajout de filtre bascule](/help/using/usage/reports-customize/t-sticky-filter.md).
* **[!UICONTROL Télécharger]**
 **[!UICONTROL un fichier PDF]** ou **[!UICONTROL CSV]** pour télécharger ou ouvrir des documents et les partager avec des utilisateurs qui n'ont pas accès à Mobile Services ou pour utiliser le fichier dans des présentations.
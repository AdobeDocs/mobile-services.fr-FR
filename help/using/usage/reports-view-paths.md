---
description: Le rapport Chemins d’accès des vues est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées entre deux états de l’application.
keywords: mobile
seo-description: Le rapport Chemins d’accès des vues est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées entre deux états de l’application.
seo-title: Afficher le rapport Chemins
solution: Marketing Cloud,Analytics
title: Afficher le rapport Chemins
topic: Rapports, Mesures
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Afficher le rapport Chemins {#view-paths}

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

![orientation du chemin d’accès](assets/view_paths_focus.png)

Vous pouvez effectuer une mise au point ou développer plusieurs nœuds afin d’obtenir une vue détaillée des chemins d’accès empruntés par les utilisateurs dans votre application. Par exemple :

![chemin d'accès](assets/view_paths_mult.png)

Vous pouvez configurer les options suivantes pour ce rapport :

* **[!UICONTROL Période]** Cliquez sur l’icône **[!UICONTROL Calendrier]** pour sélectionner une période personnalisée ou une période prédéfinie dans la liste déroulante.
* **[!UICONTROL Customize
Customize your reports by changing the Show By options, adding metrics and filters, and adding additional series (metrics), and more.]****** For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filter
Click Filter to create a filter that spans different reports to see how a segment is performing across all mobile reports.]****** Un filtre d’attractivité vous permet de définir un filtre qui est appliqué à tous les rapports autres que de cheminement. Pour plus d’informations, voir [Ajout d’un filtre](/help/using/usage/reports-customize/t-sticky-filter.md)bascule.
* **[!UICONTROL Téléchargez]** Cliquez sur **[!UICONTROL PDF]** ou **[!UICONTROL CSV]** pour télécharger ou ouvrir des documents et les partager avec des utilisateurs qui n’ont pas accès à Mobile Services ou pour utiliser le fichier dans des présentations.
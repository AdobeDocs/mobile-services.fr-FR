---
description: Le rapport Chemins d’accès des actions est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées par un état de l’application pour acquérir un autre état.
keywords: mobile
seo-description: Le rapport Chemins d’accès des actions est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées par un état de l’application pour acquérir un autre état.
seo-title: Rapport Chemins d’accès des actions
solution: Experience Cloud,Analytics
title: Rapport Chemins d’accès des actions
topic: Rapports, Mesures
uuid: a21e5d9e-fd57-4178-9d64-87181b7f988b
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Rapport Chemins d’accès des actions{#action-paths}

Le rapport Chemins d’accès des actions est basé sur l’analyse des chemins d’accès et affiche un graphique des chemins représentant les voies empruntées par un état de l’application pour acquérir un autre état.

Les rapports **[!UICONTROL Chemins d’accès des vues]** et **[!UICONTROL Chemin d’accès des actions]** sont des rapports de cheminement. Le rapport **[!UICONTROL Chemins d’accès des vues]** vous permet de visualiser la manière dont les utilisateurs naviguent d’un écran à l’autre au sein de votre application. Le rapport **[!UICONTROL Chemins d’accès des actions]** montre la séquence des actions (événements tels que des clics, sélections, redimensionnements, etc.) accomplies par les utilisateurs dans votre application.

>[!TIP]
>
>Vous pouvez utiliser un rapport Entonnoir pour combiner la navigation et les actions dans un rapport. Pour plus d’informations, reportez-vous à la section [Entonnoir](/help/using/usage/reports-funnel.md).

![](assets/action_paths.png)

Chaque nœud matérialisé par une case représente un état dans les chemins d’accès empruntés par les utilisateurs dans une application. À titre d’exemple, sur le schéma ci-dessus, le nœud supérieur représente le nombre d’utilisateurs qui ont lancé l’application, puis sélectionné une photo dans la galerie.

Pour afficher les options de modification du graphique, cliquez sur un nœud, puis sur **[!UICONTROL Mise au point]** ou **[!UICONTROL Développer]**. Si, par exemple, vous cliquez sur l’état **[!UICONTROL PhotoPicked]** dans le nœud supérieur, les icônes **[!UICONTROL Mise au point]** et **[!UICONTROL Développer]** s’affichent.

![](assets/action_paths_icons.png)

Pour agrandir l’affichage, cliquez sur l’icône **[!UICONTROL +]**. Cette option permet d’afficher les autres chemins d’accès au départ ou à destination du nœud. Sur le schéma ci-dessous, l’état 1 lance l’application, l’état 2 sélectionne une photo (l’élément que nous avons développé) et l’état 3 inclut les différents chemins d’accès empruntés par les utilisateurs :

* Sélection d’un élément
* Ajout d’un élément
* Glissement d’un élément
* Mise à l’échelle d’un élément

Le développement d’un état ressemble à un entonnoir.

![développer chemin d’action](assets/action_paths_expand.png)

Cliquez sur l’icône ![icône mise au point](assets/icon_focus.png) pour isoler le nœud et afficher les chemins d’accès entrants et sortants du nœud sélectionné. Sur le schéma ci-dessous, les chemins d’accès suivants ont été empruntés **avant** que les utilisateurs ne sélectionnent une photo :

* Rotation d’un élément
* Mise à l’échelle d’un élément
* Glissement d’un élément
* Suppression d’un élément

Les chemins d’accès suivants ont été empruntés **après** que les utilisateurs ont sélectionné la photo :

* Sélection d’un élément
* Ajout d’un élément
* Glissement d’un élément
* Mise à l’échelle d’un élément

![mise au point du chemin d’action](assets/action_paths_focus.png)

Vous pouvez effectuer une mise au point ou développer plusieurs nœuds afin d’obtenir une vue détaillée des chemins d’accès empruntés par les utilisateurs dans votre application. Par exemple :

![chemin d’action multi](assets/action_paths_mult.png)

Vous pouvez configurer les options suivantes pour ce rapport :

* **[!UICONTROL Période]**

   Cliquez sur l’icône **[!UICONTROL Calendrier]** pour sélectionner une période personnalisée ou prédéfinie dans la liste déroulante.

* **[!UICONTROL Personnaliser]**

   Personnalisez vos rapports en modifiant les options **[!UICONTROL Afficher par]**, en ajoutant des mesures et des filtres, en ajoutant des séries (mesures) supplémentaires, etc. Pour en savoir plus, voir [Personnalisation des rapports](/help/using/usage/reports-customize/reports-customize.md).

* **[!UICONTROL Filtrer]**

   Cliquez sur **[!UICONTROL Filtrer]** pour créer un filtre couvrant différents rapports, afin de visualiser le comportement d’un segment par rapport à l’ensemble des rapports mobiles. Un filtre d’attractivité vous permet de définir un filtre qui est appliqué à tous les rapports autres que de cheminement. Pour plus d’informations, voir [Ajout d’un filtre bascule](/help/using/usage/reports-customize/t-sticky-filter.md).

* **[!UICONTROL Télécharger]**

   Cliquez sur **[!UICONTROL PDF]** ou **[!UICONTROL CSV]** pour télécharger ou ouvrir les documents et les partager avec des utilisateurs qui n’ont pas accès à Mobile Services, ou pour utiliser le fichier dans des présentations.
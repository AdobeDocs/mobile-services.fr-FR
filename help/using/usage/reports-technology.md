---
description: Le rapport Technologie vous permet de visualiser les différents types d’appareils, systèmes d’exploitation, versions de système d’exploitation et opérateurs de téléphonie mobile sur lesquels votre application est utilisée.
keywords: mobile
seo-description: Le rapport Technologie vous permet de visualiser les différents types d’appareils, systèmes d’exploitation, versions de système d’exploitation et opérateurs de téléphonie mobile sur lesquels votre application est utilisée.
seo-title: Rapport Technologie
solution: Experience Cloud,Analytics
title: Rapport Technologie
topic: Reports,Metrics
uuid: 4b7322c4-8920-43cd-bb72-5a5bd515ae84
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '571'
ht-degree: 100%

---


# Rapport Technologie {#technology}

Le rapport **[!UICONTROL Technologie]** vous permet de visualiser les différents types d’appareils, systèmes d’exploitation, versions de système d’exploitation et opérateurs de téléphonie mobile sur lesquels votre application est utilisée.

Ce rapport présente une visualisation radiale de vos données existantes, et vous permet de découvrir les segments d’audience (collections de visiteurs) pour le ciblage. La création et la gestion d’audiences sont semblables à la création et à l’utilisation de segments, excepté que vous pouvez rendre les audiences disponibles dans Experience Cloud.

## Navigation et utilisation {#section_83CA60E1AE6245FEBCBFF3205615C4DF}

Cette visualisation fournit, par exemple, le rapport de base et les ventilations, utilise la hauteur pour montrer la mesure sélectionnée et les différences de performances entre les mesures. Chaque anneau représente un segment ciblé dans la catégorie de l’anneau. Vous pouvez agir sur une audience, par exemple appliquer un filtre bascule, masquer une mesure et afficher des mesures.

>[!TIP]
>
>Outre ces informations, vous pouvez afficher un tutoriel interne au produit qui décrit le mode d’interaction avec le graphique radial. Pour lancer le tutoriel, cliquez sur **[!UICONTROL Ventilation technologique]** dans la barre de titre du rapport, puis cliquez sur **[!UICONTROL Personnaliser]** et sur l’icône **[!UICONTROL i]**.

![](assets/report_technology.png)

Le graphique sous forme de cadran est interactif et vous pouvez exécuter les tâches suivantes :

* Passer la souris sur une partie quelconque du graphique pour afficher plus d’informations.
* Modifier la période en cliquant sur l’icône **[!UICONTROL Calendrier]**.
* Cliquer sur une tranche de l’anneau pour sélectionner l’audience pour laquelle vous pouvez exécuter certaines actions, notamment zoomer, masquer les audiences et créer un message in-app ou un filtre bascule.
* Dans l’angle supérieur droit, sélectionner **[!UICONTROL Type d’appareil]** et **[!UICONTROL Appareil]** pour afficher des informations sur les appareils et les types d’appareils.

* Cliquer sur une mesure secondaire sur le côté droit pour l’ajouter à la visualisation.

   Vous pouvez afficher la mesure secondaire en spécifiant la couleur, la hauteur ou les deux.

Le tableau suivant décrit les rapports standards et la manière dont ils sont alimentés dans Adobe Mobile Services :

| Rapport | Méthode de population | Description |
|--- |--- |--- |
| Device | Mesures de cycle de vie | Mesures courantes ventilées par type d’appareil. |
| Systèmes d’exploitation | Automatique | Mesures courantes ventilées par système d’exploitation. |
| Version du système d’exploitation | Mesures de cycle de vie | Mesures courantes ventilées par version du système d’exploitation. |
| Transporteurs | Automatique | Mesures courantes ventilées par opérateur. |

>[!TIP]
>
>Dans le rapport **[!UICONTROL Opérateurs]**, les utilisateurs de Wi-Fi sont identifiés comme `none`.


## Ajout de ventilations et de mesures {#section_15833511E82648869E7B1EFC24EF7B82}

Vous pouvez ajouter des ventilations et des mesures secondaires qui modifient la hauteur de chaque audience par rapport aux autres audiences du graphique.

>[!IMPORTANT]
>
>Plus vous ajoutez d’anneaux, plus le traitement prend du temps.

Pour ajouter des ventilations et des mesures secondaires, cliquez sur **[!UICONTROL Ventilation technologique]** dans la barre de titres du rapport, puis sur **[!UICONTROL Personnaliser]**.

Lorsque vous cliquez sur **[!UICONTROL Ajouter une ventilation]** ou **[!UICONTROL Ajouter une mesure]**, un nouvel élément s’affiche avec le même nom que l’élément précédent dans la liste. Cliquez sur la ventilation ou la mesure nouvellement créée pour accéder à une liste déroulante à partir de laquelle sélectionner un nouvel élément.

## Création d’un filtre d’attractivité {#section_B4E355CD1FE34E4C8ADC38139ED67FC8}

Cliquez sur une tranche de l’anneau pour sélectionner l’audience pour laquelle vous souhaitez créer un filtre d’attractivité, puis cliquez sur **[!UICONTROL Filtre bascule]**. Ce filtre permet d’appliquer les filtres actuels et d’exécuter un nouveau rapport selon les filtres.

## Partage de rapports  {#section_560DD5CED5144249B7E49461E2422100}

Une fois un rapport créé, vos paramètres sont utilisés pour créer une URL personnalisée que vous pouvez copier et partager.

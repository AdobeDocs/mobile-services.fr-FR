---
description: Lorsque vous personnalisez des rapports, la grande flexibilité qui s’offre à vous peut rendre plus complexe le choix du type de rapport adapté à la collecte des données dont vous avez besoin.
keywords: mobile
seo-description: Lorsque vous personnalisez des rapports, la grande flexibilité qui s’offre à vous peut rendre plus complexe le choix du type de rapport adapté à la collecte des données dont vous avez besoin.
seo-title: Types de rapports
solution: Experience Cloud,Analytics
title: Types de rapports
topic: Rapports, Mesures
uuid: 8747b11e-31b1-47bc-ad55-db5ab4ef7078
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Types de rapports {#report-types}

Lorsque vous personnalisez des rapports, la grande flexibilité qui s’offre à vous peut rendre plus complexe le choix du type de rapport adapté à la collecte des données dont vous avez besoin.

Avant de personnaliser des rapports, vous devez comprendre la différence entre une mesure et une dimension.

* Mesure

   Une mesure sert à mesurer vos données. Les mesures sont des valeurs qui peuvent être comptabilisées et ajoutées. Elles servent à déterminer la fréquence d’actions spécifiques dans votre application. Les mesures courantes comprennent les installations, les lancements, les recettes, les valeurs de durée de vie et les connexions. Par exemple, à chaque lancement de votre application, la valeur _launches_value augmente d’un.

* Dimension

   Une dimension sert à décrire vos données. Les dimensions sont représentées à l’aide d’une chaîne ou d’un nombre qui joue le rôle d’une chaîne (comme un code postal). Elles servent à organiser et à segmenter vos données. Les dimensions courantes comprennent la version du système d’exploitation, le nom de la campagne, le nom du produit et l’opérateur de téléphonie mobile. Chaque dimension est associée à des valeurs spécifiques. Par exemple, la dimension de version du système d’exploitation contient des valeurs telles que _iOS 7_ et _Android 4.1.2_.

Voici les types de rapports que vous pouvez générer dans l’interface utilisateur d’Adobe Mobile :

## Rapport de dépassement de délai {#section_2741DA54C90C49AFB17C7B9BC7AD627D}

Un rapport de dépassement de délai montre les performances des mesures sur une période donnée afin que vous puissiez rapidement identifier des pics et des tendances. Une analyse débute souvent dans un rapport de dépassement de délai, puis passe aux rapports de tendances et de classement à mesure que vous explorez les facteurs qui pourraient contribuer à un pic ou une tendance pour une mesure spécifique.

Si vous constatez par exemple un pic dans les lancements, vous pouvez exécuter un rapport de tendances qui affiche les lancements pour les 5 principaux systèmes d’exploitation afin de déterminer lequel contribue le plus au pic :

![](assets/overtime.png)

Pour afficher des valeurs de dimension avec d’autres mesures dans un rapport de dépassement de délai, vous pouvez utiliser la mesure d’instances et définir un filtre de dimension.

## Rapport de tendances {#section_C9BE9A2EDBFF4D938B9AF14C8AA67883}

Un rapport de tendances montre les performances de vos dimensions les plus populaires par rapport à une mesure. Ce rapport s’avère très utile pour déterminer les valeurs qui contribuent le plus à la modification d’une mesure.

![](assets/trended.png)

Pour afficher un rapport de tendances pour une dimension, ajoutez un filtre d’attractivité (Système d’exploitation = iOS 6.0.1, par exemple) à un rapport de dépassement de délai pour afficher les mêmes données. Vous pouvez en outre ajouter cinq mesures supplémentaires au rapport de dépassement de délai filtré.

## Rapport de dépassement de délai filtré {#section_F8FAF2A4496F449CA99EF1E052C71A2D}

Si vous souhaitez afficher une valeur de dimension spécifique, vous pouvez ajouter un filtre d’attractivité à un rapport de dépassement de délai. Le rapport ci-après montre 30 jours de lancements, de mises à niveau et de blocages pour une version de système d’exploitation spécifique.

![](assets/overtime-filter.png)

## Rapport de classement {#section_C073D744A95843AF99EE74FB5B013735}

Un rapport de classement permet de déterminer la fréquence de contribution des 50 principales dimensions à une mesure. Ce rapport s’avère très utile pour consulter la contribution totale pour une plage de dates donnée et un grand nombre de valeurs.

![](assets/ranked.png)

## Rapport radial {#section_17A9842039174DE094A6B1E9837E35BB}

Les rapports radiaux fournissent par exemple le rapport de base avec les ventilations. La visualisation utilise la hauteur pour montrer la mesure et les différences de performances entre les mesures. Chaque cercle concentrique représente un segment d’audience dans la catégorie correspondante. Vous pouvez exécuter des actions sur une audience, comme appliquer un filtre d’attractivité et afficher ou masquer des mesures.

Vous pouvez consulter le rapport et un tutoriel du produit qui décrit le mode d’interaction avec un graphique radial.

Pour lancer le tutoriel, procédez comme suit :

1. Dans Gérer les paramètres de l’application, cliquez sur **[!UICONTROL Utilisation]**.

1. Cliquez sur **[!UICONTROL Technologie]** &gt; **[!UICONTROL Ventilation technologique]**.
1. Dans la barre de titre du rapport, cliquez sur **[!UICONTROL Personnaliser]**, puis sur l’icône d’information.

![](assets/report_technology.png)

### Rapport de cheminement {#section_AD400106BC684B50B27CCCD3F4497114}

Un rapport de cheminement, basé sur l’analyse des chemins d’accès, affiche un graphique des chemins représentant les voies empruntées par un état de l’application pour acquérir un autre état.

![](assets/action_paths.png)

Chaque nœud matérialisé par une case représente un état dans les chemins d’accès empruntés par les utilisateurs dans une application. À titre d’exemple, sur l’illustration ci-dessus, le nœud supérieur représente le nombre d’utilisateurs qui ont lancé l’application, puis sélectionné une photo dans la galerie.

### Rapport Entonnoir {#section_AF3B0C899D844FC3AD1F91A2C452C92F}

Les rapports Entonnoir vous permettent d’identifier le moment où les clients abandonnent une campagne marketing ou se détournent d’un chemin de conversion défini lors de l’interaction avec votre application mobile. Vous pouvez également utiliser le rapport Entonnoir pour comparer les actions de différents segments.

La visualisation sous forme d’entonnoir vous permet de voir à quel moment les clients sortent du processus. L’obtention d’une bonne visibilité sur les décisions des clients à chaque étape vous permet de comprendre à quel moment ils ont été dissuadés, quel chemin ils ont tendance à emprunter, ainsi que le moment où les visiteurs quittent votre application.

![](assets/funnel.png)

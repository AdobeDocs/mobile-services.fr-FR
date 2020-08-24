---
description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-title: Extensions Windows Visual Studio pour Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Analytics
title: Extensions Windows Visual Studio pour Experience Cloud Solutions 4.x SDK
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 38e63d6f4f85c2ced6364baa47646241ac783c12
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Cette extension permet d&#39;ajouter plus facilement la référence du SDK Windows des solutions Experience Cloud 4.x dans votre projet.

## Installation de la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal depuis [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Doublon-cliquez sur le fichier **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsix]** pour ouvrir le programme d’installation.
1. Sélectionnez Emplacement **** global et installez la bibliothèque.

## ajouter des références à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 10.
1. Ouvrez la boîte de dialogue Gestionnaire de références.

   ![](assets/ref_manager.png)

1. Dans l’onglet **[!UICONTROL Extensions]** , recherchez et sélectionnez **[!UICONTROL Adobe Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le Adobe Mobile SDK sera ajouté à votre projet. Si le package **[!UICONTROL Microsoft Visual C++ Runtime]** n&#39;a pas encore été ajouté, ce package sera également ajouté à votre projet.

1. Dans Configuration Manager, sélectionnez un type de plate-forme et commencez à tester votre application.


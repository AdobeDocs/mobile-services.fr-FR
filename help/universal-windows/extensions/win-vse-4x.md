---
description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
solution: Experience Cloud,Analytics
title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---


# Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Cette extension permet d&#39;ajouter plus facilement la référence du SDK Windows des solutions Experience Cloud 4.x dans votre projet.

## Installation de la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal depuis [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Doublon-cliquez sur le fichier **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** pour ouvrir le programme d’installation.
1. Sélectionnez Emplacement **** global et installez la bibliothèque.

## Ajouter des références à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 10.
1. Ouvrez la boîte de dialogue Gestionnaire de références.

   ![](assets/ref_manager.png)

1. Dans l’onglet **[!UICONTROL Extensions]** , recherchez et sélectionnez **[!UICONTROL Adobe Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le Adobe Mobile SDK sera ajouté à votre projet. Si le package **[!UICONTROL Microsoft Visual C++ Runtime]** n&#39;a pas encore été ajouté, ce package sera également ajouté à votre projet.

1. Dans Configuration Manager, sélectionnez un type de plate-forme et commencez à tester votre application.


---
description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
solution: Experience Cloud,Analytics
title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---


# Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Ces extensions vous offrent un moyen beaucoup plus facile d&#39;ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.

## Installation de la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal depuis [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Doublon-cliquez sur le fichier ADBMobileWindowsStoreVSIX.vsix ou ADBMobileWindowsPhoneVSIX.vsix pour ouvrir le programme d’installation.

1. Sélectionnez Emplacement **** global et installez la bibliothèque.

## ajouter des références à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 8.1 ou Windows Phone 8.1.
1. Ouvrez la boîte de dialogue Gestionnaire de références.

   ![](assets/ref_manager.png)

1. Dans l’onglet **[!UICONTROL Extensions]** de Windows 8.1 ou Windows Phone 8.1, recherchez et sélectionnez **[!UICONTROL Adobe Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le Adobe Mobile SDK sera ajouté à votre projet et, s&#39;il n&#39;a pas déjà été ajouté, le package d&#39;exécution **** Microsoft Visual C++ est également ajouté.

1. Dans Configuration Manager, sélectionnez un type de plate-forme et commencez à tester votre application.


---
description: Ces extensions vous offrent un moyen beaucoup plus simple d’ajouter la référence du SDK Windows 4.x pour solutions Experience Cloud dans votre projet.
solution: Experience Cloud,Analytics
title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Ces extensions vous offrent un moyen beaucoup plus simple d’ajouter la référence du SDK Windows 4.x pour solutions Experience Cloud dans votre projet.

## Installation de la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal à partir de [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Double-cliquez sur le fichier ADBMobileWindowsStoreVSIX.vsix ou ADBMobileWindowsPhoneVSIX.vsix pour ouvrir le programme d’installation.

1. Sélectionnez **[!UICONTROL Emplacement global]** et installez la bibliothèque.

## Ajout de références à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 8.1 ou Windows Phone 8.1.
1. Ouvrez la boîte de dialogue Gestionnaire de références .

   ![](assets/ref_manager.png)

1. Dans l’onglet **[!UICONTROL Extensions]** de Windows 8.1 ou Windows Phone 8.1, recherchez et sélectionnez **[!UICONTROL Adobe Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le SDK Mobile Adobe sera ajouté à votre projet et, s’il n’a pas déjà été ajouté, le package **[!UICONTROL Microsoft Visual C++ Runtime]** est également ajouté.

1. Dans Configuration Manager, sélectionnez un type de plateforme et commencez à tester votre application.

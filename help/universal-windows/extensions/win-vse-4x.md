---
description: Ces extensions vous offrent un moyen beaucoup plus simple d’ajouter la référence du SDK Windows 4.x pour solutions Experience Cloud dans votre projet.
solution: Experience Cloud Services,Analytics
title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Cette extension permet d’ajouter plus facilement la référence du SDK Windows 4.x des solutions Experience Cloud dans votre projet.

## Installation de la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal à partir de [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Double-cliquez sur le **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** pour ouvrir le programme d’installation.
1. Sélectionner **[!UICONTROL Emplacement global]** et installez la bibliothèque .

## Ajout de références à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 10.
1. Ouvrez la boîte de dialogue Gestionnaire de références .

   ![](assets/ref_manager.png)

1. Sur le **[!UICONTROL Extensions]** , recherchez et sélectionnez **[!UICONTROL Adobe du SDK Mobile]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le SDK Mobile Adobe sera ajouté à votre projet. Si la variable **[!UICONTROL Microsoft Visual C++ Runtime]** n’a pas encore été ajouté, ce module sera également ajouté à votre projet.

1. Dans Configuration Manager, sélectionnez un type de plateforme et commencez à tester votre application.

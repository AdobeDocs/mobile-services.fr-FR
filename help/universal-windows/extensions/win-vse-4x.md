---
description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-description: Ces extensions vous offrent un moyen beaucoup plus facile d'ajouter la référence du SDK Windows 4.x de solutions Experience Cloud dans votre projet.
seo-title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
solution: Experience Cloud,Analytics
title: Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---

# Extensions de Windows Visual Studio pour le SDK 4.x des solutions Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Cette extension permet d&#39;ajouter plus facilement la référence du SDK Windows des solutions Experience Cloud 4.x dans votre projet.

## Installer la bibliothèque à partir de GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal à partir de [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez le fichier téléchargé localement.
1. Doublon-cliquez sur le fichier **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** pour ouvrir le programme d’installation.
1. Sélectionnez **[!UICONTROL Emplacement global]** et installez la bibliothèque.

## Références Ajoutées à votre projet {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez votre projet Windows 10.
1. Ouvrez la boîte de dialogue Gestionnaire de références.

   ![](assets/ref_manager.png)

1. Dans l&#39;onglet **[!UICONTROL Extensions]**, recherchez et sélectionnez **[!UICONTROL Adobe Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]** pour l’enregistrer.

   Le Adobe Mobile SDK sera ajouté à votre projet. Si le package **[!UICONTROL Microsoft Visual C++ Runtime]** n&#39;a pas encore été ajouté, ce package sera également ajouté à votre projet.

1. Dans Configuration Manager, sélectionnez un type de plate-forme et commencez à tester votre application.

---
description: Cette extension fournit un moyen beaucoup plus simple d’ajouter la référence du SDK 4.x Windows pour les solutions Experience Cloud.
seo-description: Cette extension fournit un moyen beaucoup plus simple d’ajouter la référence du SDK 4.x Windows pour les solutions Experience Cloud.
seo-title: Extensions Windows Visual Studio pour SDK 4. x d'Experience Cloud
solution: Marketing Cloud, Analytics
title: Extensions Windows Visual Studio pour SDK 4. x d'Experience Cloud
topic: Développeur et mise en œuvre
uuid: 7 d 0 ea 312-340 b -46 ea-a 737-b 70 a 6766 a 536
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Cette extension fournit un moyen beaucoup plus simple d’ajouter la référence du SDK 4.x Windows pour les solutions Experience Cloud.

## Installation de la bibliothèque à partir de github {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Téléchargez le SDK Windows Universal à partir de [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Décompressez localement le fichier téléchargé.
1. Cliquez deux fois sur le fichier adbmobilewindowsstorevsix. vsix ou adbmobilewindowsphonevsix. vsix pour ouvrir le programme d'installation.

1. Sélectionnez **[!UICONTROL l'emplacement]** global et installez la bibliothèque.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Ouvrez le projet Windows 8.1 ou Windows Phone 8.1.
1. Ouvrez la boîte de dialogue Gestionnaire de références.

   ![](assets/ref_manager.png)

1. Dans l'onglet **[!UICONTROL Extensions]** de Windows 8.1 ou Windows Phone 8.1, recherchez et sélectionnez **[UICONTROL Mobile SDK]**.
1. Cliquez sur **[!UICONTROL OK]pour l’enregistrer.**

   Le SDK Adobe Mobile est ajouté à votre projet. S'il n'a pas encore été ajouté, le package **[UICONPREVMICROSOFT Visual C + + Runtime]** est également ajouté.

1. Dans Configuration Manager, sélectionnez un type de plate-forme et commencez à tester votre application.


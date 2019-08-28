---
description: Vous pouvez créer et gérer des points ciblés, qui vous permettent de définir des emplacements géographiques que vous utiliserez aux fins de corrélation, de ciblage des messages in-app, etc. Lorsqu’un accès est envoyé dans un point ciblé, celui-ci est rattaché à l’accès en question.
keywords: mobile
seo-description: Vous pouvez créer et gérer des points ciblés, qui vous permettent de définir des emplacements géographiques que vous utiliserez aux fins de corrélation, de ciblage des messages in-app, etc. Lorsqu’un accès est envoyé dans un point ciblé, celui-ci est rattaché à l’accès en question.
seo-title: Gestion des points ciblés
solution: Marketing Cloud, Analytics
title: Gestion des points ciblés
topic: Mesures
uuid: 7 b 362534-54 fb -43 a 3-b 6 b 2-dfc 8 f 45 ff 7 c 6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

Vous pouvez créer et gérer des POI, ce qui vous permet de définir des emplacements géographiques que vous pouvez utiliser à des fins de corrélation, de ciblage avec des messages in-app, etc. Lorsqu'un accès est envoyé dans un point ciblé, le point ciblé est associé à l'accès.

Avant de pouvoir utiliser l'emplacement, vérifiez les conditions suivantes :

* Vous devez posséder les applications mobiles Analytics ou Analytics Premium.
* Vous devez activer les **[!UICONTROL rapports sur les emplacements]pour l’application.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. Sur la page Gérer les points ciblés, lorsque vous cliquez **[!UICONTROL sur Enregistrer]**, les modifications sont conditionnées à la **[!UICONTROL liste Points ciblés]** et le fichier de configuration de l'application active est mis à jour. L'enregistrement met également à jour la liste des points dans votre application sur les périphériques utilisateur, dès lors que l'application utilise le SDK et la configuration mis à jour avec une URL POI distante.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

Pour utiliser l'emplacement, effectuez les tâches suivantes :

1. Cliquez sur le nom de l’application pour accéder à sa page Gérer les paramètres de l’application.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![Résultat de l’étape](assets/poi.png)

1. Saisissez les informations dans chacun des champs suivants :

   * **[!UICONTROL Nom du point]**

      Saisissez le nom du **[!UICONTROL point ciblé.]**

      Il peut par exemple s’agir d’un nom de ville ou de région. Vous pouvez également créer un **[!UICONTROL point ciblé]à la périphérie de lieux spécifiques tels que des stades ou des entreprises.**

   * **[!UICONTROL Latitude]**

      Saisissez la latitude du **[!UICONTROL point ciblé]**. Ces informations peuvent provenir d’autres sources, y compris Internet.

   * **[!UICONTROL Longitude]**

      Saisissez la longitude du **[!UICONTROL point ciblé]**. Ces informations peuvent provenir d’autres sources, y compris Internet.

   * **[!UICONTROL Rayon (mètres)]**

      Saisissez le rayon (en mètres) autour du **[!UICONTROL point ciblé]que vous souhaitez inclure.** Par exemple, si vous créez un point ciblé pour Denver, Colorado, vous pouvez spécifier un rayon suffisamment grand pour inclure la ville de Denver et les zones environnantes, mais exclure Colorado Springs.

   * **[!UICONTROL Icône de carte]**

      Sélectionnez une icône qui s'affichera dans les rapports [Aperçu](/help/using/location/c-location-overview.md) et [Carte](/help/using/location/c-map-points.md) .

1. Ajoutez d'autres POI, si nécessaire.

   Nous vous recommandons d'ajouter plus de 5 000 POIS. Si vous ajoutez plus de 5 000 points ciblés, vous pourrez enregistrer ces points, mais vous recevrez un message d’avertissement vous informant que les règles de bonnes pratiques dictent la définition de moins de 5 000 points.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.

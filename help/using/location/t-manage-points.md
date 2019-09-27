---
description: Vous pouvez créer et gérer des points ciblés, qui vous permettent de définir des emplacements géographiques que vous utiliserez aux fins de corrélation, de ciblage des messages in-app, etc. Lorsqu’un accès est envoyé dans un point ciblé, celui-ci est rattaché à l’accès en question.
keywords: mobile
seo-description: Vous pouvez créer et gérer des points ciblés, qui vous permettent de définir des emplacements géographiques que vous utiliserez aux fins de corrélation, de ciblage des messages in-app, etc. Lorsqu’un accès est envoyé dans un point ciblé, celui-ci est rattaché à l’accès en question.
seo-title: Gestion des points ciblés
solution: Marketing Cloud,Analytics
title: Gestion des points ciblés
topic: Mesures
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

Vous pouvez créer et gérer des points d’intérêt qui vous permettent de définir des emplacements géographiques que vous pouvez utiliser à des fins de corrélation, de cibler avec des messages in-app, etc. Lorsqu’un accès est envoyé dans un point d’accès, ce dernier est associé à l’accès.

Avant d’utiliser la fonction Emplacement, vérifiez les conditions suivantes :

* Vous devez posséder les applications mobiles Analytics ou Analytics Premium.
* Vous devez activer les **[!UICONTROL rapports sur les emplacements]pour l’application.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. Sur la page Gérer les points ciblés, lorsque vous cliquez sur **[!UICONTROL Enregistrer]**, les modifications sont incluses dans la liste **[!UICONTROL Points ciblés]** et le fichier de configuration de l’application active est mis à jour. Saving also updates the list of points in your app on the user devices, as long as the app uses the updated SDK and configuration with a remote POI URL.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

Pour utiliser la commande Emplacement, procédez comme suit :

1. Cliquez sur le nom de l’application pour accéder à sa page Gérer les paramètres de l’application.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![Résultat de l’étape](assets/poi.png)

1. Entrez les informations dans chacun des champs suivants :

   * **[!UICONTROL Nom du point]**

      Saisissez le nom du **[!UICONTROL point ciblé.]**

      Il peut par exemple s’agir d’un nom de ville ou de région. Vous pouvez également créer un **[!UICONTROL point ciblé]à la périphérie de lieux spécifiques tels que des stades ou des entreprises.**

   * **[!UICONTROL Latitude]**

      Saisissez la latitude du **[!UICONTROL point ciblé]**. Ces informations peuvent provenir d’autres sources, y compris Internet.

   * **[!UICONTROL Longitude]**

      Saisissez la longitude du **[!UICONTROL point ciblé]**. Ces informations peuvent provenir d’autres sources, y compris Internet.

   * **[!UICONTROL Rayon (mètres)]**

      Saisissez le rayon (en mètres) autour du **[!UICONTROL point ciblé]que vous souhaitez inclure.** For example, if you create a POI for Denver, Colorado, you can specify a radius large enough to include the city of Denver and the surrounding areas, but exclude Colorado Springs.

   * **[!UICONTROL Icône de carte]**

      Sélectionnez une icône qui s’affichera dans les rapports [Aperçu](/help/using/location/c-location-overview.md) et [Carte](/help/using/location/c-map-points.md) .

1. Ajoutez des points d’intérêt supplémentaires, le cas échéant.

   Nous vous recommandons de n’ajouter pas plus de 5 000 POI. Si vous ajoutez plus de 5 000 points ciblés, vous pourrez enregistrer ces points, mais vous recevrez un message d’avertissement vous informant que les règles de bonnes pratiques dictent la définition de moins de 5 000 points.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.

---
description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
keywords: mobile
seo-description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
seo-title: Expérience du message in-app
solution: Marketing Cloud,Analytics
title: Expérience du message in-app
topic: Mesures
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Sur la page Expérience, saisissez le nom du message.
1. Renseignez les champs de la section **[!UICONTROL Type] :**

   * **[!UICONTROL Type
Select the message type for your in-app message campaign:]**

      * **[!UICONTROL Plein écran]**
      * **[!UICONTROL Alerte]**
      * **[!UICONTROL Notification locale]**
   * **[!UICONTROL Modèle]**

      Personnalisez un modèle de message réactif à thème pour votre message.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL Personnalisation]**

      Chargez votre contenu HTML personnalisé (plein écran seulement). Vous devez fournir un lien Clic publicitaire et un lien Annuler.

      1. Cliquez sur **[!UICONTROL Parcourir]et téléchargez un fichier HTML ou déposez un document HTML sur la fenêtre.**
      1. Cliquez sur **[!UICONTROL Télécharger des exemples]pour afficher des exemples de contenus HTML personnalisés.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. Renseignez les champs de la section **[!UICONTROL Affichage] :**

   * **[!UICONTROL Thème]**
   Sélectionnez un thème pour votre message.

   * **[!UICONTROL Mise en page]**

      Sélectionnez la mise en page de l’application sur l’écran de l’appareil.

   * **[!UICONTROL URL d’image]**

      URL d’une image. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Image groupée]**

      Chemin d’accès vers une image de votre code d’application. Cette option est utilisée lorsqu’il n’y a aucune image, ou qu’elle n’est pas disponible. Par exemple, l’image peut être indisponible si l’appareil est hors ligne. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Renseignez les champs de la section **[!UICONTROL Texte] :**

   * **[!UICONTROL En-tête]**

      Saisissez le texte pour l’en-tête du message.

   * **[!UICONTROL Contenu]**

      Saisissez le texte pour le contenu du message.

1. Renseignez les champs de la section **[!UICONTROL Boutons] :**

   * **[!UICONTROL Bouton Clic publicitaire]**

      Étiquette du bouton **[!UICONTROL Clic publicitaire].** Appuyer sur ce bouton équivaut à un clic publicitaire réussi. L’utilisateur est redirigé vers la destination.

   * **[!UICONTROL Destination]**

      Sélectionnez une destination spécifique (lien Web, profond ou hybride, par exemple) où orienter les utilisateurs lorsqu’ils cliquent sur le message. URL de redirection d’un clic publicitaire.

      Cette URL peut contenir les informations suivantes :

      * `{userId}`, qui est remplacé par l’identifiant utilisateur ou est vide lorsque l’identifiant utilisateur n’est pas défini.
      * `{trackingId}`, qui est remplacé par l'aide (correspond au cookie *s_vi* ).
      * `{messageId}`, which is replaced with the unique ID for the in-app message.
      * `{lifetimeValue}`, which is replaced with the lifetime value or 0 if no lifetime value exists.
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. Dans le cas contraire, chaque plateforme prend en charge des schémas qui vous permettent d’ouvrir ou de référencer votre application, si celle-ci a été développée pour prendre en charge le schéma personnalisé.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Seuls les **[!UICONTROL liens profonds]font l’objet d’un suivi.** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Facultatif) Pour afficher un aperçu de la mise en page de votre message, cliquez sur les icônes ci-après :

   * **[!UICONTROL Le résumé]** masque le volet d’aperçu.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Modifier l’orientation]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Pour les montres, l’orientation passe d’une face ronde à une face carrée.

   * **[!UICONTROL Aperçu sur la montre d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur la montre d’un utilisateur, cliquez sur l’icône ![de surveillance](assets/icon_watch.png).

   * **[!UICONTROL Aperçu sur le téléphone mobile d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur l’icône ![de](assets/icon_phone.png)téléphone mobile d’un utilisateur.

   * **[!UICONTROL Aperçu sur la tablette d’un utilisateur]**

      Pour prévisualiser votre message dans la tablette d’un utilisateur, cliquez sur l’icône ![de la](assets/icon_tablet.png)tablette.

      En bas du panneau d’aperçu, vous pouvez afficher une description de l’audience que vous avez sélectionnée à l’étape précédente. Vous pouvez également afficher une description de l’audience que vous avez sélectionné à l’étape précédente en bas du volet Aperçu.

1. Configurez les options [](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)Planification.

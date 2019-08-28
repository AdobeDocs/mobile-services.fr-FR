---
description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
keywords: mobile
seo-description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
seo-title: Message In-App de l'expérience
solution: Marketing Cloud, Analytics
title: Message In-App de l'expérience
topic: Mesures
uuid: 4 c 6 d 6756-47 fb -4 f 1 b -8338-0 b 0 c 9 b 0 fceb 0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Sur la page Expérience, saisissez le nom du message.
1. Renseignez les champs de la section **[!UICONTROL Type] :**

   * **[!UICONTROL Type]**
Sélectionnez le type de message pour votre campagne de messages in-app :

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

      Étiquette du bouton **[!UICONTROL Clic publicitaire].** Appuyer sur ce bouton compte comme un clic publicitaire réussi. L'utilisateur est redirigé vers la destination.

   * **[!UICONTROL Destination]**

      Sélectionnez une destination spécifique (lien Web, profond ou hybride, par exemple) où orienter les utilisateurs lorsqu’ils cliquent sur le message. URL de redirection d’un clic publicitaire.

      Cette URL peut contenir les informations suivantes :

      * `{userId}`, qui est remplacée par l'identificateur utilisateur ou vide lorsque l'identifiant utilisateur n'est pas défini.
      * `{trackingId}`, qui est remplacée par l'aid (corrélation avec *le cookie s_ vi* ).
      * `{messageId}`, qui est remplacée par l'identifiant unique du message in-app.
      * `{lifetimeValue}`, qui est remplacée par la valeur de durée de vie ou 0 s'il n'existe aucune valeur de durée de vie.
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. Dans le cas contraire, chaque plateforme prend en charge des schémas qui vous permettent d’ouvrir ou de référencer votre application, si celle-ci a été développée pour prendre en charge le schéma personnalisé.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Seuls les **[!UICONTROL liens profonds]font l’objet d’un suivi.** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Facultatif) Pour afficher un aperçu de la mise en page de votre message, cliquez sur les icônes ci-après :

   * **[!UICONTROL Le résumé]** masque le volet d'aperçu.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Modification de l'orientation]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Pour les montres, l'orientation passe d'un arrondi à un cadran carré.

   * **[!UICONTROL Aperçu sur la montre d'un utilisateur]**

      Pour afficher un aperçu de votre message tel qu'il apparaîtra sur la montre d'un utilisateur, cliquez sur l'icône ![de contrôle](assets/icon_watch.png).

   * **[!UICONTROL Aperçu sur le téléphone mobile d'un utilisateur]**

      Pour prévisualiser votre message tel qu'il apparaîtra sur l'écran d'un utilisateur, cliquez sur l'icône ![](assets/icon_phone.png)Téléphone.

   * **[!UICONTROL Aperçu sur la tablette d'un utilisateur]**

      Pour prévisualiser votre message dans la tablette d'un utilisateur, cliquez ![sur l'icône de tablette](assets/icon_tablet.png).

      En bas du panneau d’aperçu, vous pouvez afficher une description de l’audience que vous avez sélectionnée à l’étape précédente. Vous pouvez également afficher une description de l’audience que vous avez sélectionné à l’étape précédente en bas du volet Aperçu.

1. Configuration [des options de planification](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).

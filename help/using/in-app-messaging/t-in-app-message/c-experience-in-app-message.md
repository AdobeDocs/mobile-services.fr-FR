---
description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
keywords: mobile
seo-description: Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.
seo-title: 'Expérience : message in-app'
solution: Experience Cloud,Analytics
title: 'Expérience : message in-app'
topic: Mesures
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience : message in-app{#experience-in-app-message}

Configurez les options pour les messages in-app, y compris le type (plein écran, alerte ou notification) et les options d’affichage, de texte et de bouton.

1. Dans votre application, cliquez sur **[!UICONTROL Messagerie]** &gt; **[!UICONTROL Gestion des messages]** &gt; **[!UICONTROL Créer un message]** &gt; **[!UICONTROL Créer message in-app]**.
1. Sur la page Expérience, saisissez le nom du message.
1. Renseignez les champs de la section **[!UICONTROL Type] :**

   * **[!UICONTROL Type]**
Sélectionnez le type de message pour votre campagne de messages in-app :

      * **[!UICONTROL Plein écran]**
      * **[!UICONTROL Alerte]**
      * **[!UICONTROL Notification locale]**
   * **[!UICONTROL Modèle]**

      Personnalisez un modèle de message réactif à thème pour votre message.

      >[!TIP]
      >
      >Cette option est affichée uniquement quand vous sélectionnez le type de message **[!UICONTROL Plein écran]**.

   * **[!UICONTROL Personnalisation]**

      Chargez votre contenu HTML personnalisé (plein écran seulement). Vous devez fournir un lien Clic publicitaire et un lien Annuler.

      1. Cliquez sur **[!UICONTROL Parcourir]** et téléchargez un fichier HTML ou déposez un document HTML sur la fenêtre.
      1. Cliquez sur **[!UICONTROL Télécharger des exemples]** pour afficher des exemples de contenus HTML personnalisés.
      >[!TIP]
      >
      >Cette option est affichée uniquement quand vous sélectionnez le type de message **[!FPlein écran]**.



1. Renseignez les champs de la section **[!UICONTROL Affichage] :**

   * **[!UICONTROL Thème]**
   Sélectionnez un thème pour votre message.

   * **[!UICONTROL Mise en page]**

      Sélectionnez la mise en page de l’application sur l’écran de l’appareil.

   * **[!UICONTROL URL d’image]**

      URL d’une image. Si vous rencontrez des problèmes de dimensionnement lors de l’utilisation du modèle plein écran, consultez la rubrique *Mon image ne correspond pas exactement à l’espace fourni par le modèle* dans [Dépannage de la messagerie in-app](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Image groupée]**

      Chemin d’accès vers une image de votre code d’application. Cette option est utilisée lorsqu’il n’y a aucune image, ou qu’elle n’est pas disponible. Par exemple, l’image peut être indisponible si l’appareil est hors ligne. Si vous rencontrez des problèmes de dimensionnement lors de l’utilisation du modèle plein écran, consultez la rubrique *Mon image ne correspond pas exactement à l’espace fourni par le modèle* dans [Dépannage de la messagerie in-app](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Renseignez les champs de la section **[!UICONTROL Texte] :**

   * **[!UICONTROL En-tête]**

      Saisissez le texte pour l’en-tête du message.

   * **[!UICONTROL Contenu]**

      Saisissez le texte pour le contenu du message.

1. Renseignez les champs de la section **[!UICONTROL Boutons] :**

   * **[!UICONTROL Bouton Clic publicitaire]**

      Étiquette du bouton **[!UICONTROL Clic publicitaire]**. Le fait d’appuyer sur le bouton est comptabilisé comme un clic publicitaire. L’utilisateur est redirigé vers la destination.

   * **[!UICONTROL Destination]**

      Sélectionnez une destination spécifique (lien Web, profond ou hybride, par exemple) où orienter les utilisateurs lorsqu’ils cliquent sur le message. URL de redirection d’un clic publicitaire.

      Cette URL peut contenir les informations suivantes :

      * `{userId}`, qui est remplacé par l’identifiant de l’utilisateur ou reste vide si aucun identifiant n’est défini.
      * `{trackingId}`, qui est remplacé par l’aide (correspond au cookie *s_vi*).
      * `{messageId}`, qui est remplacé par l’identifiant unique du message in-app.
      * `{lifetimeValue}`, qui est remplacé par la valeur de durée de vie ou 0 s’il n’existe aucune valeur de durée de vie.
      Exemple de suivi de l’identifiant utilisateur : `https://www.mysite.com?uid={userId}`.

      Si l’adresse URL de clic publicitaire utilise l’indicatif `https://` ou `https://`, elle s’ouvre dans le navigateur du périphérique, en dehors de l’application. Dans le cas contraire, chaque plateforme prend en charge des schémas qui vous permettent d’ouvrir ou de référencer votre application, si celle-ci a été développée pour prendre en charge le schéma personnalisé.

      >[!TIP]
      >
      >Lorsque vous utilisez des types de destination de **[!UICONTROL lien Web]** ou de **[!UICONTROL lien personnalisé]**, le type de destination ne fait pas l’objet d’un suivi. Seuls les **[!UICONTROL liens profonds]** font l’objet d’un suivi. Pour plus d’informations, reportez-vous à la section [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Facultatif) Pour afficher un aperçu de la mise en page de votre message, cliquez sur les icônes ci-après :

   * **[!UICONTROL Résumé (Summary)]** masque le volet d’aperçu.

      Cliquez sur ![Aperçu](assets/icon_preview.png) pour afficher à nouveau le volet d’aperçu.

   * **[!UICONTROL Modification de l’orientation]**

      Pour permuter l’orientation de l’aperçu entre le mode portrait et le mode paysage, cliquez sur ![orientation](assets/icon_orientation.png). Pour les montres, l’orientation passe d’un cadran rond à un cadran carré.

   * **[!UICONTROL Aperçu sur la montre d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur la montre d’un utilisateur, cliquez sur ![l’icône de montre](assets/icon_watch.png).

   * **[!UICONTROL Aperçu sur le téléphone mobile d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur le téléphone mobile d’un utilisateur, cliquez sur ![l’icône de téléphone](assets/icon_phone.png).

   * **[!UICONTROL Aperçu sur la tablette d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur la tablette d’un utilisateur, cliquez sur ![l’icône de tablette](assets/icon_tablet.png).

      En bas du panneau d’aperçu, vous pouvez afficher une description de l’audience que vous avez sélectionnée à l’étape précédente. Vous pouvez également afficher une description de l’audience que vous avez sélectionné à l’étape précédente en bas du volet Aperçu.

1. Configurez les [Options de planification](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).

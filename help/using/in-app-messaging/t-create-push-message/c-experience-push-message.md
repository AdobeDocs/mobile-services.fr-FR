---
description: Vous pouvez configurer des options d’expérience pour les messages push et les messages push enrichis, notamment le nom, le texte du message et les options de destination. Vous pouvez également configurer des options avancées, notamment des options de charge utile et des options personnalisées pour les périphériques iOS.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 'Expérience : message push'
topic-fix: Metrics
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
exl-id: 9158487e-6ac5-4f17-a8ff-15de0360ab60
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 95%

---

# Experience : message push {#experience-push-message}

{#eol}

Vous pouvez configurer des options d’expérience pour les messages push et les messages push enrichis, notamment le nom, le texte du message et les options de destination. Vous pouvez également configurer des options avancées, notamment des options de charge utile et des options personnalisées pour les périphériques iOS.

1. Sur la page Audience pour un nouveau message push, cliquez sur **[!UICONTROL Experience]**.

   ![écran de message push d’experience](assets/experience-push-message.png)

1. Saisissez le nom du message.
1. Dans la section **[!UICONTROL Message]**, saisissez les informations dans les champs suivants :

   * **[!UICONTROL Contenu]**

      Spécifiez le texte de votre message. Vous pouvez spécifier jusqu’à 140 caractères.

   * **[!UICONTROL URL du média]**

      Saisissez l’URL du fichier média que vous souhaitez utiliser dans le message de notification push. Pour connaître les conditions préalables requises pour utiliser les notifications push enrichies, voir *Conditions préalables pour les notifications push enrichies* ci-dessous.

      >[!IMPORTANT]
      >
      >Pour afficher une image ou une vidéo dans une notification push, prenez note des éléments suivants :
      > * Les données `attachment-url` sont traitées dans les données utiles push.
      > * L’URL du média doit pouvoir traiter des pics de requêtes.


   * **[!UICONTROL Destination]**

      Sélectionnez une destination spécifique (lien Web, profond ou hybride, par exemple) où orienter les utilisateurs lorsqu’ils cliquent sur le message. Pour plus d’informations, reportez-vous à la section [Destinations](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >Lorsque vous utilisez les * types de destination de **[!UICONTROL lien Web]** ou de **[!UICONTROL lien personnalisé]**, le type de destination ne fait pas l’objet d’un suivi. Seuls les **[!UICONTROL liens profonds]** font l’objet d’un suivi.

## Conditions préalables pour les notifications push enrichies

Voici les conditions préalables requises pour envoyer des notifications push enrichies :

* **Versions prises en charge**

   Les notifications push enrichies sont prises en charge sur les versions suivantes :
   * Android 4.1.0 ou version ultérieure
   * iOS 10 ou version ultérieure

      >[!IMPORTANT]
      >
      >Gardez à l’esprit les informations suivantes :
      >
      >* Les messages push enrichis envoyés à des versions antérieures seront toute de même transmis, mais n’afficheront que du texte.
      >* Les montres ne sont pour l’instant pas prises en charge.


* **Formats de fichier**

   Voici les formats de fichier pris en charge :
   * Images : JPG et PNG
   * Animations (iOS uniquement) : GIF
   * Vidéos (iOS uniquement) : MP4

* **Formats d’URL**
   * HTTPS uniquement

* **Dimensions**
   * Les images doivent être au format 2:1, sinon elles sont recadrées.

Pour configurer un message push sur la page Experience :

1. (**Facultatif**) Cliquez sur le lien **[!UICONTROL Afficher les options avancées]** pour configurer des options supplémentaires :

   * **[!UICONTROL Charge utile : données]**

      Fournissez une payload push personnalisée dans JSON qui est envoyée à l’application par le biais d’une notification push ou locale. La limite pour Android et iOS est fixée à 4 ko.

   * **[!UICONTROL Options Apple : catégorie]**

      Spécifiez une catégorie pour les notifications push et locales. Pour en savoir plus, voir la section [Gestion de l’assistance concernant les notifications de votre application](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) dans la *bibliothèque de développement iOS*.

   * **[!UICONTROL Options Apple : son]**

      Spécifiez le nom du fichier audio à lire dans votre application. S’il n’est pas défini, le son d’alerte par défaut est lu. Pour en savoir plus, voir la section [Gestion de l’assistance concernant les notifications de votre application](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) dans la *bibliothèque de développement iOS*.

   * **[!UICONTROL Options Apple : contenu disponible]**

      Sélectionnez cette option de sorte qu’à la réception du message, iOS réveille votre application en arrière-plan et la laisse exécuter le code en fonction des données utiles du message. Pour en savoir plus, voir [Service de notification push Apple](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) dans la *bibliothèque de développement iOS*.

2. (Facultatif) Pour afficher un aperçu de la mise en page de votre message, cliquez sur les icônes ci-après :

   * **[!UICONTROL Résumé x]**

      Masque le volet d’aperçu. Cliquez sur ![Aperçu](assets/icon_preview.png) pour afficher à nouveau le volet d’aperçu.

   * **[!UICONTROL Modification de l’orientation]**

      Pour permuter l’orientation de l’aperçu entre le mode portrait et le mode paysage, cliquez sur ![orientation](assets/icon_orientation.png). Pour les montres, l’orientation passe d’un cadran rond à un cadran carré.

   * **[!UICONTROL Aperçu sur la montre d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur la montre d’un utilisateur, cliquez sur ![l’icône de montre](assets/icon_watch.png).

   * **[!UICONTROL Aperçu sur le téléphone mobile d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur le téléphone mobile d’un utilisateur, cliquez sur ![l’icône de téléphone](assets/icon_phone.png).

   * **[!UICONTROL Aperçu sur la tablette d’un utilisateur]**

      Pour prévisualiser votre message tel qu’il apparaîtra sur la tablette d’un utilisateur, cliquez sur ![l’icône de tablette](assets/icon_tablet.png).
   En bas du panneau d’aperçu, vous pouvez afficher une description de l’audience que vous avez sélectionnée à l’étape précédente.

3. (**Facultatif**) Cliquez sur **[!UICONTROL Test]** pour envoyer votre message en push sur les périphériques spécifiés à des fins de test.
4. Sélectionnez le service et saisissez les jetons push pour au moins un périphérique sur lequel vous souhaitez envoyer le message en push.

   Spécifiez les jetons dans une liste séparée par des virgules pour envoyer le message en push sur plusieurs périphériques.

5. Configurez les options de planification du message.

   Pour plus d’informations, voir [Planification : message push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

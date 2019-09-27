---
description: Vous pouvez créer ou modifier des liens marketing afin de fournir des liens profonds vers votre application mobile ou votre site Web.
keywords: mobile
seo-description: You can create or edit Marketing Links to provide deep linking into your mobile app or your website.
seo-title: Création ou modification de liens marketing
solution: Marketing Cloud,Analytics
title: Création ou modification de liens marketing
topic: Mesures
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Vous pouvez créer ou modifier des liens marketing pour fournir un lien profond vers votre application mobile ou votre site Web. Pour plus d’informations, voir Liens universels [Apple et Liens](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)d’application Android.

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Procédez de l’une des manières suivantes :

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Pour modifier un lien, cliquez sur son nom dans la colonne **[!UICONTROL Titre].**

1. Renseignez les champs suivants :

   * **[!UICONTROL Nom du lien marketing]**:

      (**Required**) Specify a descriptive name for your Marketing Link. Le nom s’affiche seulement sur la page Liens marketing dans l’interface utilisateur de Adobe Mobile Services. En spécifiant un nom explicite, vous et d’autres personnes de votre organisation pouvez trouver rapidement un lien spécifique et des informations à son sujet.

   * **[!UICONTROL Code de suivi unique]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. Vous pouvez afficher les rapports qui détaillent l’utilisation du code de suivi.

   * **[!UICONTROL Ajouter les données contextuelles de suivi]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. Dans la liste déroulante **[!UICONTROL Données contextuelles personnalisées], sélectionnez une balise prédéfinie ou l’une de vos propres balises.** Les données contextuelles sont utilisées pour la création de rapports lorsque le lien marketing est déployé.

      Les balises prédéfinies suivantes sont disponibles :

      * **Custom Context Data**
Specify the key and value. Si vous ajoutez des données contextuelles personnalisées, vous devez créer une règle de traitement. Pour plus d’informations, voir Présentation [des règles de](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)traitement.

      * **Source
Specify the original referrer, such as "newsletter" or "homepage."**

      * **Moyen** Spécifiez le support marketing, tel que "bannière" ou "courriel".

      * **Contenu** Indiquez le nom ou l’ID de la publicité avec le lien.

      * **Terme** Spécifiez les termes payants ou d’autres termes de recherche pour la publicité.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Renseignez les champs suivants :

   * **(Required) In Fallback URL, specify the URL that users are directed to when a destination cannot be matched (for example, if the user is on a desktop or another platform that does not match a destination rule).******
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      Pour plus d’informations, reportez-vous à la page [Spots](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) ou liens universels [Apple et liens](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)d’application Android.

   * **(Conditionnel)** Si l’option Liens **** universels ou d’application est sélectionnée, les utilisateurs peuvent, dans Chemin **** personnalisé, définir le chemin d’accès URL après le domaine à l’aide de n’importe quel paramètre de requête. For more information, see Apple Universal Links and Android App Links.[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. Si l’application est installée, une page d’entrée de spots s’affiche.

   Pour plus d’informations, voir [Spots](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. Sur la page Destination, configurez le lien.

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL Ajouter une décision]**
      * **[!UICONTROL Ajouter un chemin d’accès]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL Système d’exploitation]**

         Les systèmes d’exploitation pris en charge comprennent iOS, Android, AMX, etc.

      * **[!UICONTROL Device Type (Type de périphérique)]**

         Les types d’appareils incluent les ordinateurs de bureau, les liseuses électroniques, les consoles de jeux, les téléphones mobiles, les décodeurs, etc.
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL Boutique d’applications]**
      * **[!UICONTROL Lien Web]**
      * **[!UICONTROL Lien profond d’application]**
      * **[!UICONTROL Lien hybride]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. Pour suivre les acquisitions, utilisez le type de destination **[!UICONTROL Boutique d’applications].**

      For more information, see Create a new link destination.[](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)




1. To save the Marketing Link, click elipses and then Save.![](assets/icon_elipses.png)****

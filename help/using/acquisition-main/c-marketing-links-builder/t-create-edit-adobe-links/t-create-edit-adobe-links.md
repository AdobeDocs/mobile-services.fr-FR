---
description: Vous pouvez créer ou modifier les liens marketing afin de fournir des liens profonds vers votre application mobile ou votre site Web.
keywords: mobile
seo-description: Vous pouvez créer ou modifier les liens marketing afin de fournir des liens profonds vers votre application mobile ou votre site Web.
seo-title: Création ou modification de liens marketing
solution: Experience Cloud,Analytics
title: Création ou modification de liens marketing
topic: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 94%

---


# Création ou modification de liens marketing{#create-or-edit-marketing-links}

Vous pouvez créer ou modifier les liens marketing afin de fournir des liens profonds vers votre application mobile ou votre site Web. Pour plus d’informations, voir [Liens universels Apple et liens d’application Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Dans votre application, dans le volet de navigation de gauche, développez **[!UICONTROL Acquisition]** et cliquez sur **[!UICONTROL Générateur de liens marketing]**.
1. Procédez de l’une des manières suivantes :

   * Pour créer un lien marketing, cliquez sur **[!UICONTROL Créer]**.
   * Pour modifier un lien, cliquez sur son nom dans la colonne **[!UICONTROL Titre]**.

1. Renseignez les champs suivants :

   * **[!UICONTROL Nom du lien marketing]** :

      (**Obligatoire**) Spécifiez un nom explicite pour votre lien marketing. Le nom s’affiche seulement sur la page Liens marketing dans l’interface utilisateur de Adobe Mobile Services. En spécifiant un nom explicite, vous et d’autres personnes de votre organisation pouvez trouver rapidement un lien spécifique et des informations à son sujet.

   * **[!UICONTROL Code de suivi unique]** :

      (**Obligatoire**) Spécifiez le code de suivi souhaité ou cliquez sur ![générer une icône](assets/icon_generate.png) pour créer un nouveau code de suivi. Vous pouvez afficher les rapports qui détaillent l’utilisation du code de suivi.

   * **[!UICONTROL Ajouter les données contextuelles de suivi]** :

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. Dans la liste déroulante **[!UICONTROL Données contextuelles personnalisées]**, sélectionnez une balise prédéfinie ou l’une de vos propres balises. Les données contextuelles servent à la création de rapports lorsque le lien marketing est déployé.

      Les balises prédéfinies suivantes sont disponibles :

      * **Données contextuelles personnalisées**
Indiquez la clé et la valeur. Si vous ajoutez des données contextuelles personnalisées, vous devez créer une règle de traitement. Pour plus d’informations, voir [Aperçu des règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Source**
Spécifiez le référent original, tel que « newsletter » ou « page d’accueil ».

      * **Moyen**
Spécifiez la méthode marketing, telle que « bannière » ou « courrier électronique ».

      * **Contenu**
Spécifiez le nom ou l’identifiant de l’annonce avec le lien.

      * **Terme**
Spécifiez les termes rémunérés ou les autres termes de recherche de l’annonce considérée.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Renseignez les champs suivants :

   * **(Obligatoire)** Dans **[!UICONTROL URL de secours]**, spécifiez l’URL vers laquelle sont dirigés les utilisateurs quand une destination ne peut pas être atteinte (par exemple, si l’utilisateur a recours à un ordinateur ou à une autre plateforme qui ne correspond pas à une règle de destination)
   * Dans **[!UICONTROL Options de lien marketing]**, sélectionnez **[!UICONTROL Spots]** ou **[!UICONTROL Liens universels et d’application]**.

      Pour plus d’informations, reportez-vous à la page [Spots](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) ou [Liens universels Apple et liens d’application Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Conditionnel)** Si **[!UICONTROL Liens universels ou d’application]** est sélectionné, dans **[!UICONTROL Chemin d’accès personnalisé]**, les utilisateurs peuvent définir le chemin de l’URL suivant le domaine avec les paramètres de requête appropriés. Pour plus d’informations, voir [Liens universels Apple et liens d’application Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Cliquez sur **[!UICONTROL Modifier le spot de lien profond]** et configurez le lien.

   (**Facultatif**) Quand il existe plusieurs destinations, les utilisateurs peuvent être orientés selon qu’une application mobile est installée sur leur appareil. Si l’application est installée, un landing page interactif s’affiche.

   Pour plus d’informations, voir [Spots](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Cliquez sur **[!UICONTROL Enregistrer]** puis sur **[!UICONTROL Suivant]**.
1. Sur la page Destination, configurez le lien.

   1. Cliquez sur l’icône **[!UICONTROL Décision]** (![icône décision](assets/icon_decision.png)) et sélectionnez l’un des emplacements de décision suivants :

      * **[!UICONTROL Ajouter une décision]**
      * **[!UICONTROL Ajouter un chemin d’accès]**
   1. Si vous avez sélectionné **[!UICONTROL Ajouter une décision]**, sélectionnez l’un des types de décisions suivants :

      * **[!UICONTROL Système d’exploitation]**

         Les systèmes d’exploitation pris en charge comprennent iOS, Android, AMX, etc.

      * **[!UICONTROL Device Type]**

         Les types d’appareils incluent les ordinateurs de bureau, les liseuses électroniques, les consoles de jeux, les téléphones mobiles, les décodeurs, etc.
   1. Cliquez sur l’icône **[!UICONTROL Destination]** (![icône carrée](assets/icon_square.png) ) et sélectionnez l’un des types de destinations suivants :

      * **[!UICONTROL Boutique d’applications]**
      * **[!UICONTROL Lien Web]**
      * **[!UICONTROL Lien profond d’application]**
      * **[!UICONTROL Lien hybride]**

      >[!TIP]
      >
      >Lorsque vous utilisez le type de destination **[!UICONTROL Lien Web]** avec un lien vers la boutique d’applications, l’acquisition n’est pas suivie. Pour suivre les acquisitions, utilisez le type de destination **[!UICONTROL Boutique d’applications]**.

      Pour plus d’informations, voir [Création d’une destination de lien](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Pour enregistrer le lien marketing, cliquez sur ![les trois points](assets/icon_elipses.png), puis sur **[!UICONTROL Enregistrer]**.

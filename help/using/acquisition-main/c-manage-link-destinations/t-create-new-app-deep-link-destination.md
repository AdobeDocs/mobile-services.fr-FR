---
description: Vous pouvez créer une nouvelle destination de lien qui redirige les utilisateurs vers une page Web ou un lien profond dans votre application.
keywords: mobile
seo-description: Vous pouvez créer une nouvelle destination de lien qui redirige les utilisateurs vers une page Web ou un lien profond dans votre application.
seo-title: Création d’une destination de lien
solution: Marketing Cloud,Analytics
title: Création d’une destination de lien
topic: Mesures
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Créer une destination de lien {#create-new-link-destination}

Vous pouvez créer une nouvelle destination de lien qui redirige les utilisateurs vers une page Web ou un lien profond dans votre application.

1. In the Mobile Services UI, click **[!UICONTROL Manage Apps]**.
1. Cliquez sur le nom de l’application dont vous souhaitez afficher la page Informations sur l’application.
1. Cliquez sur **[!UICONTROL Gérer les destinations de lien]**.
1. Cliquez sur **[!UICONTROL Créer]**.
1. Renseignez les champs suivants :
   * **[!UICONTROL Titre]**

      Entrez un nom descriptif pour la destination du lien d’application. Le titre s’affiche seulement sur la page Gérer les destinations de lien dans l’interface utilisateur de Adobe Mobile Services. Grâce à ce nom explicite, vous et d’autres personnes de votre organisation pouvez trouver rapidement une destination de lien spécifique et des informations à son sujet.

   * **[!UICONTROL Type de lien]**

      Voici la liste des types de liens disponibles :

      * **[!UICONTROL Lien profond d’application]**

         Provide a URI schema deep link (for example, `yourapp://section`). Les destinations de lien profond d’application sont des liens profonds de schéma d’URI qui orientent les utilisateurs vers un lien profond au sein de l’application. Par exemple, vous pouvez diriger les utilisateurs vers une gamme de produits spécifiques dans une application mobile d’un détaillant en ligne.

      * **[!UICONTROL Lien Web]**

         Type a web HTTP or HTTPS URL, for example,`https://adobe.com`. Les destinations de lien Web orientent les utilisateurs vers une URL. Par exemple, vous pouvez rediriger les utilisateurs vers une gamme de produits sur le site Web d’une boutique en ligne.

      * **[!UICONTROL Lien hybride]**

         Type an iOS Universal Link or an Android App Link (for example, `https://yourwebsite.com`). Les liens hybrides sont compatibles avec les liens universels iOS et les liens d’application Android.
   * **[!UICONTROL Application]** Sélectionnez l’application associée au lien que vous allez fournir.

      >[!TIP]
      >
      >This information is required only if you selected an App Deep Link or a Hybrid Link in **[!UICONTROL Link Type]**. Si l’application n’apparaît pas dans la liste de sélection, cliquez sur **[!UICONTROL Ajouter une nouvelle application]afin de référencer une application à partir d’une boutique d’applications.**

   * **[!UICONTROL Type de lien]**

      Entrez l’URL réelle du lien sélectionné. Le libellé de ce champ varie selon le type de lien sélectionné.

   * **[!UICONTROL Notes]**

      Saisissez des remarques facultatives au sujet de votre destination. Ces remarques s’affichent seulement sur la page Gérer les destinations de lien dans l’interface utilisateur de Adobe Mobile Services. Elles vous aident, vous et les autres personnes de votre organisation, à rechercher rapidement une destination de lien spécifique et peuvent fournir des informations à son sujet, sur la campagne à laquelle elle est liée ou tout ce qui selon vous est important.


1. Cliquez sur **Enregistrer**.

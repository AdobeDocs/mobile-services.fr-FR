---
description: Vous pouvez créer une nouvelle destination de lien qui redirige les utilisateurs vers une page Web ou un lien profond dans votre application.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Création d’une destination de lien
topic-fix: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
exl-id: 2d2f5938-1461-43e2-a375-45c18afc9d5a
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 100%

---

# Créer une destination de lien {#create-new-link-destination}

{#eol}

Vous pouvez créer une nouvelle destination de lien qui redirige les utilisateurs vers une page Web ou un lien profond dans votre application.

1. Dans l’interface utilisateur de Mobile Services, cliquez sur **[!UICONTROL Gérer les applications]**.
1. Cliquez sur le nom de l’application dont vous souhaitez afficher la page Informations sur l’application.
1. Cliquez sur **[!UICONTROL Gérer les destinations de lien]**.
1. Cliquez sur **[!UICONTROL Créer]**.
1. Renseignez les champs suivants :
   * **[!UICONTROL Titre]**

      Saisissez un nom explicite pour la destination de lien d’application. Le titre s’affiche seulement sur la page Gérer les destinations de lien dans l’interface utilisateur de Adobe Mobile Services. Grâce à ce nom explicite, vous et d’autres personnes de votre organisation pouvez trouver rapidement une destination de lien spécifique et des informations à son sujet.

   * **[!UICONTROL Type de lien]**

      Voici la liste des types de liens disponibles :

      * **[!UICONTROL Lien profond d’application]**

         Spécifiez un lien profond de schéma d’URI (par exemple, `yourapp://section`). Les destinations de lien profond d’application sont des liens profonds de schéma d’URI qui orientent les utilisateurs vers un lien profond au sein de l’application. Par exemple, vous pouvez rediriger les utilisateurs vers une gamme de produits spécifique sur l’application mobile d’une boutique en ligne.

      * **[!UICONTROL Lien Web]**

         Saisissez une URL HTTP ou HTTPS Web, par exemple, `https://adobe.com`. Les destinations de lien Web orientent les utilisateurs vers une URL. Par exemple, vous pouvez rediriger les utilisateurs vers une gamme de produits sur le site web d’une boutique en ligne.

      * **[!UICONTROL Lien hybride]**

         Saisissez un lien universel iOS ou un lien d’application Android (par exemple, `https://yourwebsite.com`). Les liens hybrides sont compatibles avec les liens universels iOS et les liens d’application Android.
   * **[!UICONTROL Application]**
Sélectionnez l’application associée au lien que vous allez fournir

      >[!TIP]
      >
      >Ces informations sont requises seulement si vous avez sélectionné un lien profond d’application ou lien hybride dans **[!UICONTROL Type de lien]**. Si l’application n’apparaît pas dans la liste de sélection, cliquez sur **[!UICONTROL Ajouter une nouvelle application]** afin de référencer une application à partir d’une boutique d’applications.

   * **[!UICONTROL Type de lien]**

      Saisissez l’URL réelle du lien sélectionné. Le libellé de ce champ varie selon le type de lien sélectionné.

   * **[!UICONTROL Notes]**

      Saisissez des remarques facultatives au sujet de votre destination. Ces remarques s’affichent seulement sur la page Gérer les destinations de lien dans l’interface utilisateur de Adobe Mobile Services. Elles vous aident, vous et les autres personnes de votre organisation, à rechercher rapidement une destination de lien spécifique et peuvent fournir des informations à son sujet, sur la campagne à laquelle elle est liée ou tout ce qui selon vous est important.


1. Cliquez sur **Enregistrer**.

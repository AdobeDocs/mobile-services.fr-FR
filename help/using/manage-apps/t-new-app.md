---
description: Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.
keywords: mobile
seo-description: Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.
seo-title: Ajout d’une nouvelle application
solution: Marketing Cloud,Analytics
title: Ajout d’une nouvelle application
topic: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 98%

---


# Ajouter une nouvelle application {#add-a-new-app}

Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.

Ces instructions indiquent comment ajouter une nouvelle application et configurer les intégrations Adobe Analytics et Adobe Audience Manager.

Avant de pouvoir configurer votre application, vous devez l’ajouter dans l’interface utilisateur de Adobe Mobile Services. Une fois l’application créée, la configuration appropriée est générée afin d’être fournie aux développeurs qui mettent en œuvre le SDK Mobile pour l’application.

1. Connectez-vous à Adobe Mobile Services et effectuez l’une des tâches suivantes :

   * Cliquez sur **[!UICONTROL Créer]** pour créer une application.
   * Pour ajouter des applications supplémentaires, cliquez sur Gérer les applications dans le menu de navigation de gauche, puis cliquez sur **[!UICONTROL Ajouter]**.

      Pour plus d’informations sur la connexion, voir [Connexion](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Pour gérer des applications existantes, cliquez sur Gérer les applications dans le menu de navigation de gauche, puis cliquez sur l’application que vous souhaitez modifier. Vous pouvez effectuer des modifications sur la page Informations sur l’application.

1. Renseignez les champs suivants :

   **[!UICONTROL Suite de rapports]**

   Indiquez la suite de rapports dans laquelle les données de rapport seront collectées et stockées dans Adobe Analytics. Chaque application est connectée à une seule suite de rapports Analytics. Si vous envoyez des données d’application à plusieurs suites de rapports, ajoutez une nouvelle application pour chaque suite de rapports. Chaque application est connectée à une seule suite de rapports Analytics. Si vous envoyez des données d’application à plusieurs suites de rapports, ajoutez une nouvelle application pour chaque suite de rapports.

   Si vous avez hérité des droits d’administrateur Analytics dans Adobe Mobile, vous pouvez créer une suite de rapports dans Adobe Mobile. Pour créer une suite de rapports, sélectionnez **[!UICONTROL Nouvelle suite de rapports]** et renseignez les champs suivants :

   * **[!UICONTROL Identifiant de Report Suite]**

      Cet identifiant identifie de manière unique la suite de rapports dans Adobe Analytics. Le préfixe de votre société est ajouté automatiquement au début de l’identifiant.

   * **[!UICONTROL Copier les paramètres depuis]**

      Les variables, événements, règles de traitement et autres paramètres sont configurés dans la nouvelle suite de rapports exactement comme dans cette suite de rapports. Une suite de rapports créée dans Mobile Services n’est activée en ligne (ou horodatée) que si la suite de rapports **[!UICONTROL Copier les paramètres de]** utilisée était le Modèle d’applications mobiles, ou si vous créez une suite de rapports qui est activée hors ligne.

   * **[!UICONTROL Fuseau horaire]**

      Toutes les dates des rapports se trouvent dans ce fuseau horaire. Ce paramètre tente d’utiliser un fuseau horaire proche de celui utilisé par votre navigateur.

   * **[!UICONTROL Devise]**

      Les recettes sont suivies et affichées dans cette devise.
   >[!TIP]
   >
   >Pour utiliser une suite de rapports virtuelle, voir [Aperçu des suites de rapports](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Icône]**

      (**Facultatif**) Pour rechercher et sélectionner une icône pour votre application, cliquez sur **[!UICONTROL Icône]**.

   * **[!UICONTROL Nom]**

      (**Facultatif**) Saisissez un nom explicite pour l’application. Ce nom vous permet de localiser rapidement une application. Un nom significatif peut vous aider à comprendre rapidement l’objectif et les paramètres de l’application.

   * **[!UICONTROL Type]**

      Sélectionnez un type dans la liste déroulante. Les rapports disponibles qui s’affichent dans le menu de navigation de gauche varient en fonction du type d’application sélectionné.

      Vous trouverez ci-dessous les types disponibles :

      * **[!UICONTROL Standard]**

         You can leave the **[!UICONTROL Standard]** option selected for most apps.

      * **[!UICONTROL Publication]**

         Vous pouvez sélectionner cette option si votre application a été créée à l’aide d’Adobe Digital Publishing Suite.

      * **[!UICONTROL Game]**

         Cette option est similaire à l’option **[!UICONTROL Standard]**, sauf que **[!UICONTROL Game]** remplace la terminologie employée dans les rapports par des termes relatifs aux jeux. Par exemple, les utilisateurs deviennent des lecteurs. Les rapports propres aux jeux sont automatiquement affichés pour les applications de jeu.
   * **[!UICONTROL Description]**

      (**Facultatif**) Saisissez une description pour l’application.



1. Cliquez sur **[!UICONTROL Enregistrer]** pour ajouter la nouvelle application.

   Une fois l’application ajoutée, vous pouvez consulter la page Informations sur l’application pour connaître les autres options de configuration. Pour plus d’informations, voir [Gérer les paramètres d’application](/help/using/c-manage-app-settings/c-manage-app-settings.md).

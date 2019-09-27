---
description: Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.
keywords: mobile
seo-description: Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.
seo-title: Ajout d’une nouvelle application
solution: Marketing Cloud,Analytics
title: Ajout d’une nouvelle application
topic: Mesures
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Ajouter une nouvelle application{#add-a-new-app}

Utilisez ces informations pour créer une application et configurer ses mesures clés ; configurer les options du SDK pour Adobe Analytics et Adobe Audience Manager ; configurer les options d’acquisition et du service d’ID ; et télécharger le fichier de configuration, les SDK et les outils de développement et de test.

Ces instructions indiquent comment ajouter une nouvelle application et configurer les intégrations Adobe Analytics et Adobe Audience Manager.

Avant de pouvoir configurer votre application, vous devez l’ajouter dans l’interface utilisateur de Adobe Mobile Services. Une fois l’application créée, la configuration appropriée est générée afin d’être fournie aux développeurs qui mettent en œuvre le SDK Mobile pour l’application.

1. Connectez-vous à Adobe Mobile Services et effectuez l’une des tâches suivantes : 

   * Cliquez sur **[!UICONTROL Créer]pour créer une application.**
   * Pour ajouter des applications supplémentaires, cliquez sur Gérer les applications dans le menu de navigation de gauche, puis cliquez sur **[!UICONTROL Ajouter]**.

      Pour plus d’informations sur la connexion, voir [Connexion](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Pour gérer les applications existantes, cliquez sur Gérer les applications dans le menu de navigation de gauche, puis cliquez sur l’application à modifier. Vous pouvez effectuer des modifications sur la page Informations sur l’application.

1. Renseignez les champs suivants :

   **[!UICONTROL Suite de rapports]**

   Indiquez la suite de rapports dans laquelle les données de rapport seront collectées et stockées dans Adobe Analytics. Chaque application est connectée à une seule suite de rapports Analytics. Si vous envoyez des données d’application à plusieurs suites de rapports, ajoutez une nouvelle application pour chaque suite de rapports. Chaque application est connectée à une seule suite de rapports Analytics. Si vous envoyez des données d’application à plusieurs suites de rapports, ajoutez une nouvelle application pour chaque suite de rapports.

   Si vous avez hérité des droits d’administrateur Analytics dans Adobe Mobile, vous pouvez créer une suite de rapports dans Adobe Mobile. To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL Identifiant de Report Suite]**

      Cet identifiant identifie de manière unique la suite de rapports dans Adobe Analytics. Le préfixe de votre société est ajouté automatiquement au début de l’identifiant.

   * **[!UICONTROL Copier les paramètres depuis]**

      Les variables, événements, règles de traitement et autres paramètres sont configurés dans la nouvelle suite de rapports exactement comme dans cette suite de rapports. Une suite de rapports créée dans Mobile Services n’est activée en ligne (ou horodatée) que si la suite de rapports **Copier les paramètres de** utilisée était le Modèle d’applications mobiles, ou si vous créez une suite de rapports qui est activée hors ligne.

   * **[!UICONTROL Fuseau horaire]**

      Toutes les dates des rapports se trouvent dans ce fuseau horaire. Ce paramètre tente d’utiliser un fuseau horaire proche de celui utilisé par votre navigateur.

   * **[!UICONTROL Devise]**

      Les recettes sont suivies et rapportées comme ce type de devise.
   >[!TIP]
   >
   >Pour utiliser une suite de rapports virtuelle, voir Suites [de rapports](/help/using/manage-apps/c-mob-vrs.md)virtuelles.

   * **[!UICONTROL Icône]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL Nom]**

      (**Optional**) Type a descriptive name for the app. Ce nom vous permet de localiser rapidement une application. Un nom significatif peut vous aider à comprendre rapidement l’objectif et les paramètres de l’application.

   * **[!UICONTROL Type]**

      Sélectionnez un type dans la liste déroulante. Les rapports disponibles qui s’affichent dans le menu de navigation de gauche varient selon le type d’application que vous sélectionnez.

      Vous trouverez ci-dessous les types disponibles :

      * **[!UICONTROL Standard]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL Publication]**

         Vous pouvez sélectionner cette option si votre application a été créée à l’aide d’Adobe Digital Publishing Suite.

      * **[!UICONTROL Game]**

         Cette option est similaire à l’option **[!UICONTROL Standard]**, sauf que **Game]remplace la terminologie employée dans les rapports par des termes relatifs aux jeux.[!UICONTROL ** Par exemple, les utilisateurs deviennent des lecteurs. Les rapports propres aux jeux sont automatiquement affichés pour les applications de jeu.
   * **[!UICONTROL Description]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   Une fois l’application ajoutée, vous pouvez consulter la page Informations sur l’application pour connaître les autres options de configuration. For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).

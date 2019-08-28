---
description: Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.
seo-description: Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.
seo-title: Avant de commencer
solution: Marketing Cloud, Analytics
title: Avant de commencer
topic: Développeur et mise en œuvre
uuid: 04133 f 68-3618-41 fd -8 a 13-aec 5 b 6 f 04 df 6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Les administrateurs d’Analytics et les développeurs d’applications doivent procéder comme suit :

### Administrateurs d’Analytics

Pour configurer une suite de rapports et collecter les données de l’application mobile :

1. Suivez les instructions d’une des sections dans [Connexion à l’interface utilisateur Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Créez un compte Analytics pour chaque développeur d’applications.

Les développeurs d’applications ont désormais accès à l’affichage des suites de rapports que vous avez créées.

>[!IMPORTANT]
>
>Pour créer une suite de rapports et télécharger les kits SDK, vous devez être un administrateur Analytics.

### Développeurs d’applications

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

Pour plus d’informations sur les rôles et les autorisations, voir [Rôles et autorisations](/help/using/gs/c-mob-roles-and-permissions.md).

## Connexion à l’interface utilisateur Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services est l’interface principale de création de rapports pour les analyses et le ciblage des applications mobiles. Une fois que vous avez terminé ces étapes, vous pouvez télécharger un fichier de configuration préconfiguré comportant le serveur de collecte des données, la suite de rapports ainsi que de nombreux autres paramètres.

Vous pouvez vous connecter à Adobe Mobile Services de l’une des façons suivantes :

* **Experience Cloud**

   Connectez-vous à [Experience Cloud](https://marketing.adobe.com) à l’aide de votre Adobe ID.

   Cette méthode suppose que votre société a été configurée et que vous avez lié votre compte Analytics. Pour plus d'informations sur la configuration, voir [Gestion des utilisateurs et des produits](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)Experience Cloud. Pour plus d'informations sur la liaison de votre compte, voir [Organisations et liaison de comptes](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Si vous ne savez pas si votre société a été configurée dans Experience Cloud, utilisez votre compte Adobe Analytics existant.

* **Adobe Analytics**

   Cliquez sur **[!UICONTROL Se connecter avec Analytics]** et entrez votre nom d’entreprise Analytics, votre nom d’utilisateur et votre mot de passe.

## Création d’une suite de rapports {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Pour créer une suite de rapports permettant de collecter des données d’application et de définir une application, procédez comme suit :

1. Cliquez sur **[!UICONTROL Créer une application]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. Dans la liste déroulante **[!UICONTROL Suite de rapports]**, sélectionnez **[!UICONTROL Nouvelle suite de rapports]**.

1. Saisissez le nom de l’application et sélectionnez un identifiant unique de suite de rapports.

   Exemple d’identifiant de suite de rapports : `mycomobileappdev`. Vous devez configurer des suites de rapports et des applications distinctes pour les versions de développement et de production. Lorsque vous êtes prêt à configurer la version de production, répétez ces étapes.
1. Laissez le **[!UICONTROL Modèle d’applications mobiles]sélectionné.**

   Ce modèle active les horodatages afin de collecter les données hors ligne et active les variables de la solution mobile permettant de capturer les mesures de cycle de vie.

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## Téléchargement du kit SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Pour télécharger le SDK mobile :

1. Connectez-vous à Mobile Services et ouvrez votre application de l'une des manières suivantes :

   * Dans la liste déroulante **[!UICONTROL Toutes les applications], sélectionnez votre application.**
   * Dans le volet de droite, recherchez votre application et ouvrez-la.

1. Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.
1. Faites défiler la liste jusqu’à la section **[!UICONTROL Téléchargements de SDK d’application]**.****

1. Téléchargez le SDK et l’exemple d’application correspondant à votre plateforme.

>[!TIP]
>
>Un fichier de configuration pour votre application est automatiquement inclus dans le téléchargement du SDK. Vous n'avez donc pas besoin de télécharger ce fichier séparément. Néanmoins, si vous avez déjà téléchargé le SDK et que vous souhaitez obtenir les paramètres mis à jour, téléchargez de nouveau le fichier de configuration.


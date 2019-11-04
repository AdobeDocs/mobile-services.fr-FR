---
description: Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.
seo-description: Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.
seo-title: Avant de commencer
solution: Experience Cloud,Analytics
title: Avant de commencer
topic: Développeur et mise en œuvre
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Avant de commencer{#before-you-start}

Suivez les étapes ci-après pour configurer une suite de rapports afin de collecter des données d’application iOS.

## Tâches spécifiques à un rôle {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Les administrateurs d’Analytics et les développeurs d’applications doivent procéder comme suit :

### Administrateurs d’Analytics

Pour configurer une suite de rapports et collecter les données de l’application mobile :

1. Suivez les instructions d’une des sections dans [Connexion à l’interface utilisateur Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Créez un compte Analytics pour chaque développeur d’applications.

Les développeurs d’applications ont désormais accès à l’affichage des suites de rapports que vous avez créées.

>[!IMPORTANT]
>
>Pour créer une suite de rapports et télécharger les SDK, vous devez être un administrateur d’Analytics.

### Développeurs d’applications

1. Assurez-vous que votre administrateur d’Analytics a suivi les étapes de la section *Administrateurs d’Analytics* ci-dessus.

1. Assurez-vous que votre administrateur d’Analytics a suivi les instructions d’une des sections dans *Connexion à l’interface utilisateur Adobe Mobile Services* ci-dessous.
1. Une fois la suite de rapports configurée, suivez les étapes de la rubrique *Téléchargement du SDK* ci-dessous.

Pour plus d’informations sur les rôles et les autorisations, voir [Rôles et autorisations](/help/using/gs/c-mob-roles-and-permissions.md).

## Connexion à l’interface utilisateur Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services est l’interface principale de création de rapports pour les analyses et le ciblage des applications mobiles. Une fois que vous avez terminé ces étapes, vous pouvez télécharger un fichier de configuration préconfiguré comportant le serveur de collecte des données, la suite de rapports ainsi que de nombreux autres paramètres.

Vous pouvez vous connecter à Adobe Mobile Services de l’une des façons suivantes :

* **Experience Cloud**

   Connectez-vous à [Experience Cloud](https://marketing.adobe.com) à l’aide de votre Adobe ID.

   Cette méthode suppose que votre société a été configurée et que vous avez lié votre compte Analytics. Pour plus d’informations sur la configuration, voir [Gestion des utilisateurs et des produits Experience Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/admin-getting-started.html). Pour plus d’informations sur la liaison de votre compte, voir [Liaisons d’organisations et de comptes](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Si vous ne savez pas si votre entreprise dispose de privilèges d’accès dans Experience Cloud, utilisez votre compte Adobe Analytics existant.

* **Adobe Analytics**

   Cliquez sur **[!UICONTROL Se connecter avec Analytics]** et entrez votre nom d’entreprise Analytics, votre nom d’utilisateur et votre mot de passe.

## Création d’une suite de rapports {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Pour créer une suite de rapports permettant de collecter des données d’application et de définir une application, procédez comme suit :

1. Cliquez sur **[!UICONTROL Créer une application]**.

   Si ce bouton n’est pas visible, cliquez sur **[!UICONTROL Gérer les applications]** &gt; **[!UICONTROL Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Suite de rapports]**, sélectionnez **[!UICONTROL Nouvelle suite de rapports]**.

1. Saisissez le nom de l’application et sélectionnez un identifiant unique de suite de rapports.

   Exemple d’identifiant de suite de rapports : `mycomobileappdev`. Vous devez configurer des suites de rapports et des applications distinctes pour les versions de développement et de production. Lorsque vous êtes prêt à configurer la version de production, répétez ces étapes.
1. Laissez le **[!UICONTROL Modèle d’applications mobiles]** sélectionné.

   Ce modèle active les horodatages afin de collecter les données hors ligne et active les variables de la solution mobile permettant de capturer les mesures de cycle de vie.

1. Sélectionnez votre **[!UICONTROL Fuseau horaire]** et votre **[!UICONTROL Devise]**, puis cliquez sur **[!UICONTROL Enregistrer]**.

## Téléchargement du kit SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Pour télécharger le SDK mobile :

1. Connectez-vous à Mobile Services et ouvrez votre application de l’une des façons suivantes :

   * Dans la liste déroulante **[!UICONTROL Toutes les applications]**, sélectionnez votre application.
   * Dans le volet de droite, recherchez votre application et ouvrez-la.

1. Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.
1. Faites défiler la liste jusqu’à la section **[!UICONTROL Téléchargements de SDK d’application]******.

1. Téléchargez le SDK et l’exemple d’application correspondant à votre plateforme.

>[!TIP]
>
>Un fichier de configuration correspondant à votre application est automatiquement inclus dans le téléchargement du SDK : ainsi, vous n’avez pas besoin de télécharger ce fichier séparément. Néanmoins, si vous avez déjà téléchargé le SDK et que vous souhaitez obtenir les paramètres mis à jour, téléchargez de nouveau le fichier de configuration.


---
description: 'Avant de configurer une suite de rapports et de collecter les données des applications Android, effectuez les tâches prérequises suivantes '
seo-description: 'Avant de configurer une suite de rapports et de collecter les données des applications Android, effectuez les tâches prérequises suivantes '
seo-title: Avant de commencer
solution: Marketing Cloud,Analytics
title: Avant de commencer
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: ht
source-git-commit: 0720b2004097eb288bd8f59723eeb09a79dd81e7

---


# Avant de commencer {#before-you-start}

Avant de configurer une suite de rapports et de collecter les données des applications Android, effectuez les tâches prérequises suivantes :

## Tâches spécifiques à un rôle {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Les administrateurs d’Analytics et les développeurs d’applications doivent procéder comme suit :

### Administrateurs d’Analytics

Pour configurer une suite de rapports et collecter les données de l’application mobile :

1. Suivez les instructions d’une des sections dans [Connexion à l’interface utilisateur Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Créez un compte Analytics pour chaque développeur d’applications.

Les développeurs d’applications ont désormais accès à l’affichage des suites de rapports que vous avez créées.

>[!IMPORTANT]
>
>Pour créer une suite de rapports et télécharger les SDK, vous devez être un administrateur d’Analytics.

### Développeurs d’applications

1. Assurez-vous que votre administrateur d’Analytics a suivi les étapes de la *Administrateurs d’Analytics* dans [Tâches spécifiques à un rôle](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).
1. Assurez-vous que votre administrateur d’Analytics a suivi les instructions d’une des sections dans [Connexion à l’interface utilisateur Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Une fois la suite de rapports configurée, suivez les étapes de la rubrique [Téléchargement du SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Pour plus d’informations sur les rôles et les autorisations, voir [Rôles et autorisations](/help/using/gs/c-mob-roles-and-permissions.md).

## Connexion à l’interface utilisateur Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services est l’interface principale de création de rapports pour les analyses et le ciblage des applications mobiles. Une fois que vous avez terminé ces étapes, vous pouvez télécharger un fichier de configuration préconfiguré comportant le serveur de collecte des données, la suite de rapports ainsi que de nombreux autres paramètres.

Vous pouvez vous connecter à l’interface utilisateur Adobe Mobile Services de l’une des façons suivantes :

### Experience Cloud

Connectez-vous à [Experience Cloud](https://marketing.adobe.com) à l’aide de votre Adobe ID. Cette méthode suppose que votre entreprise a reçu les privilèges d’accès dans Experience Cloud et que vous avez lié votre compte Analytics. Pour plus d’informations, voir [Gestion des utilisateurs et des produits Experience Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Si vous ne savez pas si votre entreprise dispose de privilèges d’accès dans Experience Cloud, utilisez votre compte Adobe Analytics existant.

### Adobe Analytics

Cliquez sur **[!UICONTROL Se connecter avec Analytics]** et entrez votre nom d’entreprise Analytics, votre nom d’utilisateur et votre mot de passe.

## Création d’une suite de rapports {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Pour créer une suite de rapports permettant de collecter des données d’application et de définir une application, procédez comme suit :

1. Connectez-vous à l’interface utilisateur Mobile Services en saisissant [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) dans un navigateur.
1. Cliquez sur **[!UICONTROL Créer une application]**.

   Si ce bouton n’est pas visible, cliquez sur **[!UICONTROL Gérer les applications]** > **[!UICONTROL  Ajouter]**.

1. Dans la liste déroulante **[!UICONTROL Suite de rapports]**, sélectionnez **[!UICONTROL  Nouvelle suite de rapports]**.

1. Saisissez le nom de l’application et sélectionnez un type de suite de rapports.

   Exemple d’identifiant de suite de rapports : `mycomobileappdev`. Vous devez configurer des suites de rapports et des applications distinctes pour les versions de développement et de production, afin de pouvoir répéter ces étapes lorsque vous êtes prêt à configurer la version de production.
1. Dans **[!UICONTROL Identifiant de suite de rapports]**, vérifiez que le nom de votre suite de rapports est affiché.
1. Dans **[!UICONTROL Copier les paramètres de]**, vérifiez que **[!UICONTROL  Modèle d’applications mobiles]** est sélectionné.

   Ce modèle active les horodatages afin de collecter les données hors ligne et active les variables de la solution mobile permettant de capturer les mesures de cycle de vie.

1. Sélectionnez votre fuseau horaire et votre devise, puis cliquez sur **[!UICONTROL Enregistrer]**.

## Téléchargement du kit SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Pour télécharger le SDK mobile :

1. Connectez-vous à l’interface utilisateur Mobile Services en saisissant [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) dans un navigateur.
1. Dans le volet de gauche, cliquez sur la liste déroulante **[!UICONTROL Toutes les applications]** et sélectionnez votre application.
Vous pouvez également sélectionner votre application dans le volet de droite.

   >[!IMPORTANT]
   >
   >Pour afficher votre application dans le volet de droite, vous devez d’abord créer une application. Pour plus d’informations sur la création d’une application, voir [Ajout d’une nouvelle application.](https://docs.adobe.com/content/help/fr-FR/mobile-services/using/manage-apps-ug/t-new-app.html)

1. Dans votre application, dans le volet de gauche, cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.

   >[!IMPORTANT]
   >
   >Si vous ne voyez pas l’option **[!UICONTROL Gérer les paramètres de l’application]**, vérifiez que vous êtes connecté à Adobe Mobile Services. Pour vérifier, cliquez sur l’icône du ![sélecteur de solution](assets/solution-switcher.png) dans le coin supérieur droit de la page et assurez-vous qu’**[!UICONTROL  Adobe Mobile Services]** s’affiche dans le coin supérieur gauche.

1. Au bas de la page Gestion des paramètres de l’application, dans la section **[!UICONTROL Téléchargements du SDK d’application]**, téléchargez le SDK et l’exemple d’application pour votre plateforme.

>[!TIP]
>
>Un fichier de configuration correspondant à votre application est automatiquement inclus dans le téléchargement du SDK : ainsi, vous n’avez pas besoin de télécharger ce fichier séparément. Néanmoins, si vous avez déjà téléchargé le SDK et que vous souhaitez obtenir les paramètres mis à jour, téléchargez de nouveau le fichier de configuration.

Si vous utilisez Android Studio, vous pouvez également ajouter l’instruction suivante au fichier `build.gradle` de votre application :

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

À noter :

* Remplacez le numéro de version de l’exemple de code par la version appropriée des SDK Android.
* Téléchargez le fichier de configuration et incluez-le dans votre projet.
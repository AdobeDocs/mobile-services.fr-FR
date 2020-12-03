---
description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
seo-description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
seo-title: Rôles et autorisations
title: Rôles et autorisations
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 53%

---


# Rôles et autorisations{#roles-and-permissions}

Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.

## Aperçu {#section_91B8192891E14E5285718C8118912500}

Les rôles suivants gèrent les autorisations dans l’interface utilisateur de Mobile Services :

### Votre administrateur Analytics

Un administrateur Analytics gère les groupes d’utilisateurs et affecte des autorisations, dont l’un est l’administrateur des applications mobiles. L’administrateur Experience Cloud lie votre Adobe ID à votre compte Adobe Analytics, ce qui vous permet de vous connecter à l’interface utilisateur de Mobile Services à l’aide de votre Adobe ID. Pour plus d’informations sur l’administrateur Experience Cloud, voir [Administration - Gestion des utilisateurs et FAQ](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Un administrateur Analytics existant a la possibilité d’affecter un rôle d’administrateur Analytics à n’importe quel utilisateur.

Pour plus d’informations sur ce rôle, consultez le contenu suivant :

* [Gestion des utilisateurs - Aperçu](https://docs.adobe.com/content/help/fr-FR/analytics/admin/user-product-management/user-management/users.html)

* [Modifications des autorisations d’utilisateur et des droits d’accès de groupe](https://docs.adobe.com/content/help/fr-FR/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administration des applications mobiles

Ce rôle confère les droits d’administrateur pour l’interface utilisateur de Mobile Services.

>[!IMPORTANT]
>
>Pour certaines fonctionnalités, telles que la messagerie push, l’administrateur Analytics doit cocher la case **[!UICONTROL Création de segments]** dans Gestion des utilisateurs.

## Gestion des accès {#section_E6939C2695AA4A0DBF432D50B2670920}

Voici quelques informations complémentaires sur l’accès aux options dans l’interface utilisateur de Mobile Services :

### Applications et suites de rapports

Toutes les applications Mobile Service sont liées aux suites de rapports. Si les utilisateurs n’ont pas accès à une suite de rapports, ils n’auront pas accès à l’application associée à cette suite de rapports.

### Fonctionnalités Mobile Services et Analytics

Si votre société ne dispose pas de contrat Analytics pour accéder à une fonctionnalité de l’interface utilisateur, comme la messagerie push, aucun utilisateur de votre entreprise ne pourra accéder à cette fonctionnalité, quel que soit son niveau d’accréditation.

## Rôles et autorisations{#section_20AA029D5B8C413C8659777E79B11620}

Voici les rôles de l’interface utilisateur de Mobile Services, accompagnés de leurs autorisations pertinentes :

### Votre administrateur Analytics

* Affecter les autorisations d’administrateur pour tous les utilisateurs et toutes les applications mobiles
* Créer une application avec une nouvelle suite de rapports
* Supprimer l’application de Mobile Services

   >[!IMPORTANT]
   >
   >Bien que l’application soit supprimée dans l’interface utilisateur de Mobile Services, la suite de rapports existe toujours dans Analytics.

* Gérer les paramètres de l’application

   * Activer le Rapports de cycle de vie
   * Activer le Rapports d&#39;emplacement
   * Créer/Mettre à jour/Supprimer des variables et des mesures

### Administration des applications mobiles

* Toutes les autorisations d’utilisateur
* Créer une application avec une suite de rapports existante
* Gérer les paramètres de l’application

   * Configuration des options Mobile SDK de l’application
   * Configuration des paramètres de l’interface utilisateur de l’application
   * Configuration d’applications App Store liées
   * Configuration des options de lien universel de l’application
   * Configuration des certificats et clés d’API des services Push
   * Créer/Mettre à jour/Activer/Désactiver/Duplicata/Archiver/Supprimer des postbacks
   * Créer/Mettre à jour/Archiver/Supprimer des destinations de lien

* Créer/Mettre à jour/Archiver des liens marketing
* Créer/Importer/Mettre à jour/Supprimer des liens d’acquisition hérités
* Configuration Créer/Importer/Mettre à jour/Supprimer des emplacements (points ciblés)
* Créer/Mettre à jour/Envoyer/Programmer/Annuler/Duplicata/Archiver/Supprimer des messages Push
* Créer/Mettre à jour/Activer/Désactiver/Duplicata/Archiver/Supprimer des messages in-app

Pour plus d’informations sur les groupes et les utilisateurs, voir :

* [Paramètres du groupe d’utilisateurs](https://docs.adobe.com/content/help/fr-FR/analytics/admin/user-product-management/user-groups/groups.html)
* [Ajout d’un utilisateur à un groupe](https://docs.adobe.com/content/help/fr-FR/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Utilisateur de Mobile Services

Ce rôle dispose d’autorisations de vue uniquement et peut fournir des commentaires dans l’interface utilisateur de Mobile Services.

* Fournir des commentaires sur l’interface utilisateur de Mobile Services
* Applications de vue

   >[!IMPORTANT]
   >
   >Les utilisateurs peuvent uniquement voir les suites de rapports auxquelles ils ont accès dans Adobe Analytics.

* Paramètres de l’application vue

   * Téléchargement de la configuration du SDK d’application
   * Vue de tous les paramètres de l’interface utilisateur et du SDK
   * Configuration des variables et mesures de vue
   * Report vue
   * Destinations des liens de vue

* Affichage et exécution des rapports
* Afficher les liens marketing
* Vue et exportation des liens d’acquisition hérités
* Configuration des lieux de vue et d’exportation (points ciblés)
* Messages push vue
* Messages in-app de vue

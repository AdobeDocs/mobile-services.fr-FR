---
description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
title: Rôles et autorisations
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 42%

---

# Rôles et autorisations{#roles-and-permissions}

Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.

## Présentation {#section_91B8192891E14E5285718C8118912500}

Les rôles suivants gèrent les autorisations dans l’interface utilisateur de Mobile Services :

### Votre administrateur Analytics

Un administrateur Analytics gère les groupes d’utilisateurs et affecte des autorisations, dont l’un est l’administrateur des applications mobiles. L’administrateur Experience Cloud associe votre Adobe ID à votre compte Adobe Analytics, ce qui vous permet de vous connecter à l’interface utilisateur de Mobile Services à l’aide de votre Adobe ID. Pour plus d’informations sur l’administrateur Experience Cloud, voir [Gestion des utilisateurs et des produits Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) dans le guide des composants de l’interface centrale Experience Cloud.

>[!TIP]
>
>Un administrateur Analytics existant a la possibilité d’affecter un rôle d’administrateur Analytics à n’importe quel utilisateur.

Pour plus d’informations sur ce rôle, voir le contenu suivant dans la documentation Adobe Analytics :

* [Gestion des utilisateurs - Aperçu](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/users.html)
* [Modifications des autorisations d’utilisateur et des droits d’accès de groupe](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administration des applications mobiles

Ce rôle confère les droits d’administrateur pour l’interface utilisateur de Mobile Services.

>[!IMPORTANT]
>
>Pour certaines fonctionnalités, telles que la messagerie push, l’administrateur Analytics doit cocher la case **[!UICONTROL Création de segments]** dans Gestion des utilisateurs.

## Gestion des accès {#section_E6939C2695AA4A0DBF432D50B2670920}

Voici quelques informations complémentaires sur l’accès aux options dans l’interface utilisateur de Mobile Services :

### Applications et suites de rapports

Toutes les applications Mobile Service sont liées à des suites de rapports. Si les utilisateurs n’ont pas accès à une suite de rapports, ils n’auront pas accès à l’application associée à cette suite.

### Fonctionnalités Mobile Services et Analytics

Si votre société ne dispose pas de contrat Analytics pour accéder à une fonctionnalité de l’interface utilisateur, comme la messagerie push, aucun utilisateur de votre entreprise ne pourra accéder à cette fonctionnalité, quel que soit son niveau d’accréditation.

## Rôles et autorisations {#section_20AA029D5B8C413C8659777E79B11620}

Voici les rôles de l’interface utilisateur de Mobile Services, accompagnés de leurs autorisations pertinentes :

### Votre administrateur Analytics permissions

* Affecter les autorisations d’administrateur pour tous les utilisateurs et toutes les applications mobiles
* Créer une application avec une nouvelle suite de rapports
* Suppression d’une application de Mobile Services

   >[!IMPORTANT]
   >
   >Bien que l’application soit supprimée dans l’interface utilisateur de Mobile Services, la suite de rapports existe toujours dans Analytics.

* Gérer les paramètres de l’application

   * Activation des rapports du cycle de vie
   * Activation des rapports d’emplacement
   * Création/mise à jour/suppression de variables et de mesures

### Administration des applications mobiles permissions

* Toutes les autorisations d’utilisateur
* Créer une application avec une suite de rapports existante
* Gérer les paramètres de l’application

   * Configuration des options du SDK Mobile de l’application
   * Configuration des paramètres de l’interface utilisateur de l’application
   * Configuration des applications de la boutique d’applications liées
   * Configuration des options de lien universel de l’application
   * Configuration des certificats de services push et des clés d’API
   * Créer/mettre à jour/activer/désactiver/dupliquer/archiver/supprimer des postbacks
   * Créer/mettre à jour/archiver/supprimer des destinations de lien

* Créer/mettre à jour/archiver des liens marketing
* Créer/importer/mettre à jour/supprimer des liens d’acquisition hérités
* Configuration Créer/Importer/Mettre à jour/Supprimer des emplacements (points ciblés)
* Créer/Mettre à jour/Envoyer/Planifier/Annuler/Dupliquer/Archiver/Supprimer des messages push
* Créer/mettre à jour/activer/désactiver/dupliquer/archiver/supprimer des messages In-App

Pour plus d’informations sur les groupes et les utilisateurs, consultez le contenu suivant dans la documentation Adobe Analytics :

* [Paramètres du groupe d’utilisateurs (hérités)](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-groups/groups.html)
* [Ajout d’un utilisateur à un groupe](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Utilisateur de Mobile Services

Ce rôle dispose d’autorisations d’affichage uniquement et peut fournir des commentaires dans l’interface utilisateur de Mobile Services.

* Fournir des commentaires sur l’interface utilisateur de Mobile Services
* Afficher les applications

   >[!IMPORTANT]
   >
   >Les utilisateurs peuvent uniquement voir les suites de rapports auxquelles ils ont accès dans Adobe Analytics.

* Afficher les paramètres de l’application

   * Téléchargement de la configuration du SDK de l’application
   * Affichage de tous les paramètres de l’interface utilisateur et du SDK
   * Affichage de la configuration des variables et des mesures
   * Afficher les postbacks
   * Affichage des destinations de lien

* Affichage et exécution des rapports
* Afficher les liens marketing
* Affichage et exportation de liens d’acquisition hérités
* Afficher et exporter la configuration des emplacements (points ciblés)
* Affichage des messages push
* Affichage des messages in-app

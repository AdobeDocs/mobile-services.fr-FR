---
description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
seo-description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
seo-title: Rôles et autorisations
title: Rôles et autorisations
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.

## Aperçu {#section_91B8192891E14E5285718C8118912500}

Les rôles suivants gèrent les autorisations dans l’interface utilisateur de Mobile Services :

### Votre administrateur Analytics

Un administrateur Analytics gère les groupes d’utilisateurs et affecte les autorisations (l’une d’elles concernant l’administrateur des applications mobiles). L’administrateur Experience Cloud lie votre Adobe ID à votre compte Adobe Analytics. Vous pouvez ainsi vous connecter à l’interface utilisateur de Mobile Services à l’aide de votre Adobe ID. Pour en savoir plus sur l’administrateur d’Experience Cloud, voir [Administration – Gestion des utilisateurs et FAQ](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Un administrateur Analytics existant peut affecter le rôle d’administrateur Analytics à n’importe quel utilisateur.

Pour plus d’informations sur ce rôle, consultez le contenu suivant :

* [Présentation de la gestion des utilisateurs](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [Modifications des autorisations d’utilisateur et de groupe](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administration des applications mobiles

Ce rôle confère les droits d’administrateur pour l’interface utilisateur de Mobile Services.

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

Voici quelques informations complémentaires sur l’accès aux options dans l’interface utilisateur de Mobile Services :

### Applications et suites de rapports

Toutes les applications de Mobile Services sont liées aux suites de rapports. Si les utilisateurs n’ont pas accès à une suite de rapports, ils ne pourront pas accéder à l’application rattachée à cette suite de rapports.

### Mobile Services and Analytics features

Si votre société ne dispose pas de contrat Analytics pour accéder à une fonctionnalité de l’interface utilisateur, comme la messagerie push, aucun utilisateur de votre entreprise ne pourra accéder à cette fonctionnalité, quel que soit son niveau d’accréditation.

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

Voici les rôles de l’interface utilisateur de Mobile Services, accompagnés de leurs autorisations pertinentes :

### Votre administrateur Analytics

* All User and Mobile App Admin Permissions
* Créer une application avec une nouvelle suite de rapports
* Supprimer une application de Mobile Services

   >[!IMPORTANT]
   >
   >Although the app has been deleted in the Mobile Services UI, the report suite still exists in Analytics.

* Gérer les paramètres de l’application

   * Activer les rapports sur le cycle de vie
   * Activer les rapports sur les emplacements
   * Créer/Mettre à jour/Supprimer des variables et des mesures

### Administration des applications mobiles

* Affecter les autorisations pour tous les utilisateurs
* Créer une application avec une suite de rapports existante
* Gérer les paramètres de l’application

   * Configurer les options du SDK mobile d’une application
   * Configurer les paramètres de l’interface utilisateur de l’application
   * Configurer les applications liées de la boutique d’applications
   * Configurer les options de lien universel d’une application
   * Configurer les certificats de services push et les clés API
   * Créer/mettre à jour/activer/désactiver/dupliquer/archiver/supprimer les postbacks
   * Créer/mettre à jour/archiver/supprimer les destinations de lien

* Créer/mettre à jour/archiver les liens marketing
* Créer/importer/mettre à jour/supprimer les liens d’acquisition hérités
* Créer/importer/mettre à jour/supprimer la configuration des emplacements (points ciblés)
* Créer/mettre à jour/envoyer/programmer/annuler/dupliquer/archiver/supprimer les messages push
* Créer/mettre à jour/activer/désactiver/dupliquer/archiver/supprimer les messages in-app

Pour plus d’informations sur les groupes et les utilisateurs, voir :

* [User group settings](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Ajout d’un utilisateur à un groupe](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services user

Ce rôle dispose d’un droit en lecture seule et peut formuler des commentaires dans l’interface utilisateur de Mobile Services.

* Formuler des commentaires sur l’interface utilisateur de Mobile Services
* Afficher les applications

   >[!IMPORTANT]
   >
   >Les utilisateurs peuvent uniquement afficher les suites de rapports auxquelles ils ont accès dans Adobe Analytics.

* Afficher les paramètres d’application

   * Télécharger la configuration du SDK de l’application
   * Afficher toutes les interfaces utilisateur et tous les SDK
   * Afficher la configuration des variables et des mesures
   * Afficher les postbacks
   * Afficher les destinations de lien

* Affichage et exécution des rapports
* Afficher les liens marketing
* Afficher et exporter les liens d’acquisition hérités
* Afficher et exporter la configuration des emplacements (points ciblés)
* Afficher les messages push
* Afficher les messages in-app

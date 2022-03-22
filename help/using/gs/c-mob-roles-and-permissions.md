---
description: Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.
title: Rôles et autorisations
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 46%

---

# Rôles et autorisations{#roles-and-permissions}

Dans Adobe Analytics, vous pouvez gérer les rôles sur la page d’accueil des outils d’administration.

## Présentation {#section_91B8192891E14E5285718C8118912500}

Les rôles suivants gèrent les autorisations dans l’interface utilisateur de Mobile Services :

### Administrateur Analytics

An Analytics Admin manages user groups and assigns permissions, one of which is the Mobile App Admin. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=fr)

>[!TIP]
>
>Un administrateur Analytics existant a la possibilité d’affecter un rôle d’administrateur Analytics à n’importe quel utilisateur.

### Administrateur des applications mobiles

Ce rôle confère les droits d’administrateur pour l’interface utilisateur de Mobile Services.

>[!IMPORTANT]
>
>Pour certaines fonctionnalités, telles que la messagerie push, l’administrateur Analytics doit cocher la case **[!UICONTROL Création de segments]** dans Gestion des utilisateurs.

## Gestion des accès {#section_E6939C2695AA4A0DBF432D50B2670920}

Voici quelques informations complémentaires sur l’accès aux options dans l’interface utilisateur de Mobile Services :

### Applications et suites de rapports

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Fonctionnalités Mobile Services et Analytics

Si votre société ne dispose pas de contrat Analytics pour accéder à une fonctionnalité de l’interface utilisateur, comme la messagerie push, aucun utilisateur de votre entreprise ne pourra accéder à cette fonctionnalité, quel que soit son niveau d’accréditation.

## Rôles et autorisations {#section_20AA029D5B8C413C8659777E79B11620}

Voici les rôles de l’interface utilisateur de Mobile Services, accompagnés de leurs autorisations pertinentes :

### Administrateur Analytics autorisations

* Affecter les autorisations d’administrateur pour tous les utilisateurs et toutes les applications mobiles
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >Bien que l’application soit supprimée dans l’interface utilisateur de Mobile Services, la suite de rapports existe toujours dans Analytics.

* Gérer les paramètres de l’application

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### Administrateur des applications mobiles autorisations

* All User Permissions
* Create App with existing report suite
* Gérer les paramètres de l’application

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=fr)
* [Ajout d’un utilisateur à un groupe](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Utilisateur de Mobile Services

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >Les utilisateurs peuvent uniquement voir les suites de rapports auxquelles ils ont accès dans Adobe Analytics.

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* Affichage et exécution des rapports
* Afficher les liens marketing
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages

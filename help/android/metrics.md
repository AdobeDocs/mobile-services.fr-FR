---
description: Mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Mesures de cycle de vie
topic-fix: Developer and implementation
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
exl-id: 1e50318d-894c-4039-ba45-71cb9edbc5b5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 100%

---

# Mesures de cycle de vie{#lifecycle-metrics}

Cette section donne des informations sur les mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre. Pour plus d’informations sur le dépannage, consultez [Données de durée de vie de dépannage](https://helpx.adobe.com/fr/analytics/kb/troubleshoot-lifecycle-data.html).

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Mesures et dimensions de cycle de vie {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois les mesures de cycle de vie configurées, elles sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox, et transmises en tant que signal à la gestion de l’audience. Analytics et Target utilisent le même format, tandis que la gestion de l’audience utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi de cycle de vie sont automatiquement capturées et consignées à l’aide de la mesure ou de la dimension répertoriée, et les exceptions sont notées.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Données contextuelles Analytics/Paramètre Target : `a.InstallEvent`
   * Signal d’Audience Manager : `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Données contextuelles Analytics/Paramètre Target : `a.UpgradeEvent`
   * Signal d’Audience Manager : `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target : `a.DailyEngUserEvent`
   * Signal d’Audience Manager : `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target : `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager : `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la mise en premier plan de l’application lorsque le délai d’expiration de la session de cycle de vie a été dépassé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target : `a.LaunchEvent`
   * Signal d’Audience Manager : `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage.  La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Données contextuelles Analytics/Paramètre Target : `a.CrashEvent`
   * Signal d’Audience Manager : `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Données contextuelles Analytics/Paramètre Target : `a.PrevSessionLength`
   * Signal d’Audience Manager : `c_a_PrevSessionLength`


### Dimensions

* **La date d’installation**

   Date du premier lancement après installation. Le format de date est MM/JJ/AAAA.

   * Données contextuelles Analytics/Paramètre Target : `a.InstallDate`
   * Audience Manager : `c_a_InstallDate`

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant `[AppName] [BundleVersion]`. Exemple de ce format : `myapp 1.1`.

   * Données contextuelles Analytics/Paramètre Target : `a.AppID`
   * Audience Manager : `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Données contextuelles Analytics/Paramètre Target : `a.Launches`
   * Audience Manager : `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceFirstUse`
   * Audience Manager : `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceLastUse`
   * Audience Manager : `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée.  Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Données contextuelles Analytics/Paramètre Target : `a.HourOfDay`
   * Audience Manager : `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Données contextuelles Analytics/Paramètre Target : `a.DayOfWeek`
   * Audience Manager : `c_a_DayOfWeek`

* **Version du système d’exploitation**

   La version du système d’exploitation.

   * Données contextuelles Analytics/Paramètre Target : `a.OSVersion`
   * Audience Manager : `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceLastUpgrade`
   * Audience Manager : `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.LaunchesSinceUpgrade`
   * Audience Manager : `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Données contextuelles Analytics/Paramètre Target : `a.DeviceName`
   * Audience Manager : `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.  Important : Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.CarrierName`
   * Audience Manager : `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Données contextuelles Analytics/Paramètre Target : `a.Resolution`
   * Audience Manager : `c_a_Resolution`

## Mesures et dimensions mobiles supplémentaires {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans les variables des solutions mobiles par la méthode répertoriée dans la colonne **Description**.

### Mesures

* **Durée totale de l’action**

   Renseigné par les méthodes `trackTimedAction`.

   * Données contextuelles Analytics/Paramètre Target : `a.action.time.total`
   * Caractéristique d’Audience Manager : `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Renseigné par les méthodes `trackTimedAction`.

   * Données contextuelles Analytics/Paramètre Target : `a.action.time.inapp`
   * Caractéristique d’Audience Manager : `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Renseigné par les méthodes `trackLifetimeValue`.

   * Données contextuelles Analytics/Paramètre Target : `a.ltv.amount`
   * Caractéristique d’Audience Manager : `c_a_ltv_amount`

### Dimensions

* **Lieu (jusqu’à 10 km)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètres Target :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes trackLocation.

   * Données contextuelles Analytics/Paramètres Target :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Renseigné par les méthodes trackLocation.

   * Données contextuelles Analytics/Paramètres Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil se trouve dans le point ciblé défini.

   * Données contextuelles Analytics/Paramètres Target : `a.loc.poi`
   * Caractéristique d’Audience Manager : `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil se trouve dans le point ciblé défini.

   * Données contextuelles Analytics/Paramètres Target : `a.loc.dist`
   * Caractéristique d’Audience Manager : `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseignée par les méthodes trackLifetimeValue.

   * Données contextuelles Analytics/Paramètres Target : `a.ltv.amount`
   * Caractéristique d’Audience Manager : `c_a_ltv_amount`

* **Code de suivi**

   Renseigné par l’acquisition des applications mobiles et généré automatiquement par Adobe Mobile Services.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.trackingcode`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nom de la campagne, également stocké dans la variable de campagne. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.name`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_name`

* **Contenu de campagne**

   Le nom ou l’identifiant du contenu qui a affiché le lien. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.content`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_content`

* **Support de campagne**

   Support marketing, une bannière ou un email par exemple. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.medium`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_medium`

* **Source de campagne**

   Référent original, comme une newsletter ou les médias sociaux. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.source`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_source`

* **Termes de campagne**

   Mots-clés ou autres termes payés dont vous souhaitez effectuer le suivi avec cette acquisition. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètres Target : `a.referrer.campaign.term`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_term`

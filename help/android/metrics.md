---
description: Mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre.
keywords: android;library;mobile;sdk
seo-description: Mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre.
seo-title: Mesures de cycle de vie
solution: Marketing Cloud,Analytics
title: Mesures de cycle de vie
topic: Développeur et mise en œuvre
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Lifecycle metrics{#lifecycle-metrics}

Cette section fournit des informations sur les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile, une fois le cycle de vie mis en oeuvre, et un lien pour résoudre les problèmes liés aux données de cycle de vie. Pour plus d’informations sur le dépannage, consultez [Dépannage des données](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)de cycle de vie.

## Nouvelle version du SDK mobile Adobe Experience Platform

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, accédez à Adobe Experience Platform Launch.
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois configurées, les mesures de cycle de vie sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox et en tant que signal pour la gestion de l’audience. Analytics et Target utilisent le même format, tandis que la gestion de l’audience utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi du cycle de vie sont automatiquement capturées dans la mesure ou la dimension et font l’objet de rapports à l’aide de celle-ci, et les exceptions sont notées.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Données contextuelles Analytics/Paramètre Target: `a.InstallEvent`
   * Signal d’Audience Manager: `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Données contextuelles Analytics/Paramètre Target: `a.UpgradeEvent`
   * Signal d’Audience Manager: `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target: `a.DailyEngUserEvent`
   * Signal d’Audience Manager: `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target: `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager: `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la reprise depuis l’arrière-plan de l’application lorsque le délai d’expiration de la session du cycle de vie a été dépassé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target: `a.LaunchEvent`
   * Signal d’Audience Manager: `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage.  La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Données contextuelles Analytics/Paramètre Target: `a.CrashEvent`
   * Signal d’Audience Manager: `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Données contextuelles Analytics/Paramètre Target: `a.PrevSessionLength`
   * Signal d’Audience Manager: `c_a_PrevSessionLength`


### Dimensions

* **la date d’installation**

   Date du premier lancement après installation. Le format de date est MM/JJ/AAAA.

   * Données contextuelles Analytics/Paramètre Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID d’application**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. An example of this format is `myapp 1.1`.

   * Données contextuelles Analytics/Paramètre Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Données contextuelles Analytics/Paramètre Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Données contextuelles Analytics/Paramètre Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Données contextuelles Analytics/Paramètre Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée.  Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Données contextuelles Analytics/Paramètre Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Données contextuelles Analytics/Paramètre Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Version du système d’exploitation**

   Version du système d’exploitation.

   * Données contextuelles Analytics/Paramètre Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Données contextuelles Analytics/Paramètre Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.  Important : Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Données contextuelles Analytics/Paramètre Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans les variables des solutions mobiles par la méthode répertoriée dans la colonne **Description**.

### Mesures

* **Durée totale de l’action**

   Populated by `trackTimedAction` methods.

   * Données contextuelles Analytics/Paramètre Target: `a.action.time.total`
   * Caractéristique d’Audience Manager : `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Populated by `trackTimedAction` methods.

   * Données contextuelles Analytics/Paramètre Target: `a.action.time.inapp`
   * Caractéristique d’Audience Manager : `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Populated by `trackLifetimeValue` methods.

   * Données contextuelles Analytics/Paramètre Target: `a.ltv.amount`
   * Caractéristique d’Audience Manager : `c_a_ltv_amount`

### Dimensions

* **Lieu (jusqu’à 10 km)**

   Populated by `trackLocation` methods.

   * Paramètres Analytics Context Data/Target :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes trackLocation.

   * Paramètres Analytics Context Data/Target :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Renseigné par les méthodes trackLocation.

   * Paramètres Analytics Context Data/Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristiques d’Audience Manager :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil se trouve dans le point ciblé défini.

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Caractéristique d’Audience Manager : `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil se trouve dans le point ciblé défini.

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Caractéristique d’Audience Manager : `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseignée par les méthodes trackLifetimeValue.

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Caractéristique d’Audience Manager : `c_a_ltv_amount`

* **Code de suivi**

   Renseigné par l’acquisition des applications mobiles et généré automatiquement par Adobe Mobile Services.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nom de la campagne, également stocké dans la variable de campagne. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_name`

* **Contenu de campagne**

   Le nom ou l’identifiant du contenu qui a affiché le lien. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_content`

* **Support de campagne**

   Support marketing, une bannière ou un courrier électronique par exemple. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_medium`

* **Source de campagne**

   Référent original, une newsletter ou un réseau de médias sociaux par exemple. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_source`

* **Termes de campagne**

   Mots-clés ou autres termes payés dont vous souhaitez effectuer le suivi avec cette acquisition. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Caractéristique d’Audience Manager : `c_a_referrer_campaign_term`

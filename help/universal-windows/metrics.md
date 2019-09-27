---
description: Répertorie les mesures et les dimensions qui peuvent être automatiquement mesurées par la bibliothèque mobile.
keywords: android;library;mobile;sdk
seo-description: Répertorie les mesures et les dimensions qui peuvent être automatiquement mesurées par la bibliothèque mobile.
seo-title: Mesures de cycle de vie
solution: Marketing Cloud,Analytics
title: Mesures de cycle de vie
topic: Développeur et mise en œuvre
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics {#lifecycle-metrics}

Répertorie les mesures et les dimensions qui peuvent être automatiquement mesurées par la bibliothèque mobile.

For more information, see Troubleshoot Lifecycle data.[](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois configurées, les mesures de cycle de vie sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox et en tant que signal pour la gestion de l’audience. Analytics et Target utilisent le même format, tandis que la gestion de l’audience utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi du cycle de vie sont automatiquement capturées dans et signalées à l’aide de la mesure ou de la dimension. Exceptions are noted in the content.

## Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la reprise depuis l’arrière-plan de l’application lorsque le délai d’expiration de la session du cycle de vie a été dépassé.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage. La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`


## Dimensions

* **la date d’installation**

   Date du premier lancement après installation. The date format is .`MM/DD/YYYY`

   * Analytics Context Data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **ID d’application**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. An example of this format is `myapp 1.1`.

   * Analytics Context Data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Analytics Context Data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Analytics Context Data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée. Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Analytics Context Data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Analytics Context Data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **Version du système d’exploitation**

   The OS version.

   * Analytics Context Data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics Context Data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Analytics Context Data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics Context Data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Analytics Context Data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

The following metrics and dimensions are captured in mobile solution variables by the following method:

### Mesures

* **Durée totale de l’action**

   Populated by `trackTimedAction` methods.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Manager signal: `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Populated by `trackTimedAction` methods.
   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Manager signal: `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Manager signal: `c_a_ltv_amount`

### Dimensions

* **Lieu (jusqu’à 10 km)**

   Populated by `trackLocation` methods.

   * Paramètre(s) Données contextuelles Analytics/Target :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager trait(s):

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Populated by `trackLocation` methods.

   * Paramètre(s) Données contextuelles Analytics/Target :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager trait(s):

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Populated by `trackLocation` methods.

   * Paramètre(s) Données contextuelles Analytics/Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager trait(s):

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes `trackLocation` lorsque l’appareil est dans un point ciblé défini.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes `trackLocation` lorsque l’appareil se trouve dans le point ciblé défini.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`

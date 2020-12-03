---
description: Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.
keywords: android;library;mobile;sdk
seo-description: Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.
seo-title: Mesures de cycle de vie
solution: Experience Cloud,Analytics
title: Mesures de cycle de vie
topic: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 63%

---


# Mesures de cycle de vie {#lifecycle-metrics}

Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.

Pour plus d’informations, voir [Résolution des problèmes liés aux données](https://helpx.adobe.com/fr/analytics/kb/troubleshoot-lifecycle-data.html)du cycle de vie.

## Mesures et dimensions de cycle de vie {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois configurées, les mesures de cycle de vie sont envoyées dans des paramètres de données contextuelles à Analytics, dans des paramètres à Cible avec chaque appel de mbox et en tant que signal à l’Audience Manager. Analytics et Cible utilisent le même format et l’Audience Manager utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi du cycle de vie sont automatiquement capturées dans la mesure ou la dimension répertoriée ci-dessous et font l’objet de rapports à l’aide de celle-ci, et des exceptions sont notées.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Signal d’Audience Manager : `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Signal d’Audience Manager : `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!TIP]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Signal d’Audience Manager : `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager : `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la mise en premier plan de l’application lorsque le délai d’expiration de la session de cycle de vie a été dépassé.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Signal d’Audience Manager : `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage. La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Signal d’Audience Manager : `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Signal d’Audience Manager : `c_a_PrevSessionLength`

### Dimensions

* **La date d’installation**

   Date du premier lancement après installation. Le format de date est `MM/DD/YYYY`.

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager : `c_a_InstallDate`

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant `[AppName] [BundleVersion]`. Exemple de ce format : `myapp 1.1`.

   * Analytics context data/Target: `a.AppID`
   * Audience Manager : `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Analytics context data/Target: `a.Launches`
   * Audience Manager : `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager : `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager : `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée. Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager : `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager : `c_a_DayOfWeek`

* **Version du système d’exploitation**

   La version du système d’exploitation.

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager : `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager : `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager : `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager : `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager : `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager : `c_a_Resolution`


## Mesures et dimensions mobiles supplémentaires {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans des variables de solution mobile par les méthodes répertoriées dans la description.

### Mesures

* **Durée totale de l’action**

   Renseigné par les méthodes `trackTimedAction`.

   * Analytics context data/Target parameter: `a.action.time.total`
   * Audience Manager trait: `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Renseigné par les méthodes `trackTimedAction`.

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Audience Manager trait: `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Renseigné par les méthodes `trackLifetimeValue`.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`

## Dimensions

* **Lieu (jusqu’à 10 km)**

   Renseigné par les méthodes `trackLocation`.

   * Paramètre de Cible/données contextuelles Analytics :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caractéristique de l&#39;Audience Manager :

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes `trackLocation`.

   * Paramètre de Cible/données contextuelles Analytics :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristique de l&#39;Audience Manager :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Renseigné par les méthodes `trackLocation`.

   * Paramètre de Cible/données contextuelles Analytics :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristique de l&#39;Audience Manager :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics context data/Target parameter: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics context data/Target parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseigné par les méthodes `trackLifetimeValue`.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`

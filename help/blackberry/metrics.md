---
description: Mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre.
keywords: android;library;mobile;sdk
solution: Experience Cloud,Analytics
title: Mesures de cycle de vie
topic-fix: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
exl-id: d7436411-65bd-4cf7-ae3e-cec829a7690a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 78%

---

# Mesures de cycle de vie {#lifecycle-metrics}

Mesures et dimensions pouvant être évaluées automatiquement par la bibliothèque mobile une fois le cycle de vie ainsi qu’un lien pour dépanner les données du cycle de vie mis en œuvre.

Pour plus d’informations, consultez la base de connaissances à l’adresse [Dépannage des données du cycle de vie](https://helpx.adobe.com/fr/analytics/kb/troubleshoot-lifecycle-data.html).

## Mesures et dimensions de cycle de vie {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois les mesures de cycle de vie configurées, elles sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox, et transmises en tant que signal à la gestion de l’audience. Analytics et Target utilisent le même format, tandis que la gestion de l’audience utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi de cycle de vie sont automatiquement capturées et consignées à l’aide de la mesure ou de la dimension.

### Mesures

* **a.media.name**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Données contextuelles Analytics/Paramètre Target : `a.InstallEvent`
   * Signal d’Audience Manager : `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Données contextuelles Analytics/Paramètre Target : `a.UpgradeEvent`
   * Signal d’Audience Manager : `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target : `a.DailyEngUserEvent`
   * Signal d’Audience Manager : `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.  &quot;&quot;

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Données contextuelles Analytics/Paramètre Target : `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager : `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la mise en premier plan de l’application lorsque le délai d’expiration de la session de cycle de vie a été dépassé.

   * Données contextuelles Analytics/Paramètre Target : `a.LaunchEvent`
   * Signal d’Audience Manager : `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage. La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Données contextuelles Analytics/Paramètre Target : `a.CrashEvent`
   * Signal d’Audience Manager : `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Données contextuelles Analytics/Paramètre Target : `a.PrevSessionLength`
   * Signal d’Audience Manager : `c_a_PrevSessionLength`

### Dimensions

* **La date d’installation**

   Date du premier lancement après installation. Le format de date est `MM/DD/YYYY`.

   * Données contextuelles Analytics/Paramètre Target : `a.InstallDate`
   * Signal d’Audience Manager : `c_a_InstallDate`

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant :   
   `[AppName] [BundleVersion]`.

   Exemple de ce format : `myapp 1.1`.

   * Données contextuelles Analytics/Paramètre Target : `a.AppID`
   * Signal d’Audience Manager : `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Données contextuelles Analytics/Paramètre Target : `a.Launches`
   * Signal d’Audience Manager : `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceFirstUse`
   * Signal d’Audience Manager : `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceLastUse`
   * Signal d’Audience Manager : `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée. Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Données contextuelles Analytics/Paramètre Target : `a.HourOfDay`
   * Signal d’Audience Manager : `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Données contextuelles Analytics/Paramètre Target : `a.DayOfWeek`
   * Signal d’Audience Manager : `c_a_DayOfWeek`

* **Version du système d’exploitation**

   Version du système d’exploitation.

   * Données contextuelles Analytics/Paramètre Target : `a.OSVersion`
   * Signal d’Audience Manager : `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.DaysSinceLastUpgrade`
   * Signal d’Audience Manager : `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.LaunchesSinceUpgrade`
   * Signal d’Audience Manager : `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Données contextuelles Analytics/Paramètre Target : `a.DeviceName`
   * Signal d’Audience Manager : `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Données contextuelles Analytics/Paramètre Target : `a.CarrierName`
   * Signal d’Audience Manager : `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Données contextuelles Analytics/Paramètre Target : `a.Resolution`
   * Signal d’Audience Manager : `c_a_Resolution`

## Mesures et dimensions mobiles supplémentaires {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans les variables de solution mobile par la méthode répertoriée.

* **Lieu (jusqu’à 10 km)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes `trackLocation` lorsque l’appareil se trouve dans un point ciblé défini.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.poi`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_poi`


* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes `trackLocation` lorsque l’appareil se trouve dans un point ciblé défini.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.dist`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_dist`

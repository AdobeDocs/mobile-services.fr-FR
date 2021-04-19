---
description: Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.
keywords: android;library;mobile;sdk
seo-description: Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.
seo-title: Mesures de cycle de vie
solution: Experience Cloud,Analytics
title: Mesures de cycle de vie
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 63%

---

# Mesures de cycle de vie {#lifecycle-metrics}

Liste les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile.

Pour plus d’informations, voir [Dépannage des données de cycle de vie](https://helpx.adobe.com/fr/analytics/kb/troubleshoot-lifecycle-data.html).

## Mesures et dimensions de cycle de vie {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois configurées, les mesures de cycle de vie sont envoyées dans des paramètres de données contextuelles à Analytics, dans des paramètres à Cible avec chaque appel de mbox et en tant que signal à l’Audience Manager. Analytics et Cible utilisent le même format et l’Audience Manager utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi du cycle de vie sont automatiquement capturées dans la mesure ou la dimension répertoriée ci-dessous et font l’objet de rapports à l’aide de celle-ci, et des exceptions sont notées.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Paramètre de Cible/données contextuelles Analytics : `a.InstallEvent`
   * Signal d’Audience Manager : `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après une mise à niveau ou lorsque le numéro de version change.

   * Paramètre de Cible/données contextuelles Analytics : `a.UpgradeEvent`
   * Signal d’Audience Manager : `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!TIP]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Paramètre de Cible/données contextuelles Analytics : `a.DailyEngUserEvent`
   * Signal d’Audience Manager : `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

   * Paramètre de Cible/données contextuelles Analytics : `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager : `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la mise en premier plan de l’application lorsque le délai d’expiration de la session de cycle de vie a été dépassé.

   * Paramètre de Cible/données contextuelles Analytics : `a.LaunchEvent`
   * Signal d’Audience Manager : `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au démarrage de l’application après son blocage. La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Paramètre de Cible/données contextuelles Analytics : `a.CrashEvent`
   * Signal d’Audience Manager : `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Paramètre de Cible/données contextuelles Analytics : `a.PrevSessionLength`
   * Signal d’Audience Manager : `c_a_PrevSessionLength`

### Dimensions

* **La date d’installation**

   Date du premier lancement après installation. Le format de date est `MM/DD/YYYY`.

   * Cible/données contextuelles Analytics : `a.InstallDate`
   * Audience Manager : `c_a_InstallDate`

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant `[AppName] [BundleVersion]`. Exemple de ce format : `myapp 1.1`.

   * Cible/données contextuelles Analytics : `a.AppID`
   * Audience Manager : `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Cible/données contextuelles Analytics : `a.Launches`
   * Audience Manager : `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Cible/données contextuelles Analytics : `a.DaysSinceFirstUse`
   * Audience Manager : `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

   * Cible/données contextuelles Analytics : `a.DaysSinceLastUse`
   * Audience Manager : `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée. Cette mesure utilise le format numérique de 24 heures et est utilisée pour le découpage temporel afin de déterminer les pics horaires d’utilisation.

   * Cible/données contextuelles Analytics : `a.HourOfDay`
   * Audience Manager : `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Cible/données contextuelles Analytics : `a.DayOfWeek`
   * Audience Manager : `c_a_DayOfWeek`

* **Version du système d’exploitation**

   La version du système d’exploitation.

   * Cible/données contextuelles Analytics : `a.OSVersion`
   * Audience Manager : `c_a_OSVersion`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Cible/données contextuelles Analytics : `a.DaysSinceLastUpgrade`
   * Audience Manager : `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Cible/données contextuelles Analytics : `a.LaunchesSinceUpgrade`
   * Audience Manager : `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.

   * Cible/données contextuelles Analytics : `a.DeviceName`
   * Audience Manager : `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   >[!IMPORTANT]
   >
   >Cette mesure n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

   * Cible/données contextuelles Analytics : `a.CarrierName`
   * Audience Manager : `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Cible/données contextuelles Analytics : `a.Resolution`
   * Audience Manager : `c_a_Resolution`


## Mesures et dimensions mobiles supplémentaires {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans des variables de solution mobile par les méthodes répertoriées dans la description.

### Mesures

* **Durée totale de l’action**

   Renseigné par les méthodes `trackTimedAction`.

   * Paramètre de Cible/données contextuelles Analytics : `a.action.time.total`
   * Caractéristique de l&#39;Audience Manager : `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Renseigné par les méthodes `trackTimedAction`.

   * Paramètre de Cible/données contextuelles Analytics : `a.action.time.inapp`
   * Caractéristique de l&#39;Audience Manager : `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Renseigné par les méthodes `trackLifetimeValue`.

   * Paramètre de Cible/données contextuelles Analytics : `a.ltv.amount`
   * Caractéristique de l&#39;Audience Manager : `c_a_ltv_amount`

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

   Renseigné par des méthodes `trackLocation` lorsque le périphérique se trouve dans un point d’intérêt défini.

   * Paramètre de Cible/données contextuelles Analytics : `a.loc.poi`
   * Caractéristique de l&#39;Audience Manager : `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par des méthodes `trackLocation` lorsque le périphérique se trouve dans un point d’intérêt défini.

   * Paramètre de Cible/données contextuelles Analytics : `a.loc.dist`
   * Caractéristique de l&#39;Audience Manager : `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseigné par les méthodes `trackLifetimeValue`.

   * Paramètre de Cible/données contextuelles Analytics : `a.ltv.amount`
   * Caractéristique de l&#39;Audience Manager : `c_a_ltv_amount`

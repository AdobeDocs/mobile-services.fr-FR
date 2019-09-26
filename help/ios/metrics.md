---
description: Les tableaux suivants répertorient les mesures et les dimensions pouvant être mesurées automatiquement par la bibliothèque mobile une fois la mise en œuvre du cycle de vie terminée.
seo-description: Les tableaux suivants répertorient les mesures et les dimensions pouvant être mesurées automatiquement par la bibliothèque mobile une fois la mise en œuvre du cycle de vie terminée.
seo-title: Mesures de cycle de vie
solution: Marketing Cloud,Analytics
title: Mesures de cycle de vie
topic: Développeur et mise en œuvre
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# Lifecycle metrics {#lifecycle-metrics}

Voici les mesures et dimensions qui peuvent être automatiquement mesurées par la bibliothèque mobile une fois le cycle de vie mis en oeuvre.

## New Adobe Experience Platform Mobile SDK Release

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to [Experience Platform Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois les mesures de cycle de vie configurées, elles sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox, et transmises en tant que signal à Audience Manager. Analytics et Target utilisent le même format, tandis qu’Audience Manager utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi de cycle de vie sont automatiquement capturées et consignées à l’aide de la mesure ou de la dimension répertoriée dans la première colonne.

>[!TIP]
>
>Exceptions are provided in the description.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après mise à niveau ou dès que le numéro de version change.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché à la reprise depuis l’arrière-plan de l’application une fois le délai d’expiration de la session du cycle de vie dépassé.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au redémarrage de l’application après son plantage.  La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> The Daily Engaged Users and Monthly Engaged Users metrics are not automatically stored in an Analytics metric. **** You must create a processing rule that sets a custom event to capture these metrics.

#### Dimensions

* **la date d’installation**

   Date du premier lancement après installation.  The date format is `MM/DD/YYYY`.

   * Données contextuelles Analytics/Paramètre: `a.InstallDate`
   * Gestion de l’audience: `c_a_InstallDate`

* **ID d’application**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. Par exemple : `myapp 1.1`.

   * Données contextuelles Analytics/Paramètre: `a.AppID`
   * Gestion de l’audience: `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Données contextuelles Analytics/Paramètre: `a.Launches`
   * Gestion de l’audience: `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Données contextuelles Analytics/Paramètre: `a.DaysSinceFirstUse`
   * Gestion de l’audience: `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière exécution.

   * Données contextuelles Analytics/Paramètre: `a.DaysSinceLastUse`
   * Gestion de l’audience: `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure de lancement de l’application suivant le format numérique de 24 heures. Utilisée pour le découpage temporel afin de déterminer les heures hautes d’utilisation.

   * Données contextuelles Analytics/Paramètre: `a.HourOfDay`
   * Gestion de l’audience: `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Données contextuelles Analytics/Paramètre: `a.DayOfWeek`
   * Gestion de l’audience: `c_a_DayOfWeek`

* **Version du système d’exploitation**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   * Données contextuelles Analytics/Paramètre: `a.OSVersion`
   * Gestion de l’audience: `c_a_OSVersion|OS version`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis la dernière mise à niveau.

   * Données contextuelles Analytics/Paramètre: `a.DaysSinceLastUpgrade`
   * Gestion de l’audience: `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   * Données contextuelles Analytics/Paramètre: `a.LaunchesSinceUpgrade`
   * Gestion de l’audience: `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.  Chaîne de deux chiffres séparés par une virgule qui identifie l’appareil iOS. Le premier chiffre représente généralement la génération de l’appareil, le second les différents membres de la famille d’appareils. Pour obtenir la liste des noms d’appareils courants, reportez-vous à  Versions des appareils iOS.

   * Données contextuelles Analytics/Paramètre: `a.DeviceName`
   * Gestion de l’audience: `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   * Données contextuelles Analytics/Paramètre: `a.CarrierName`
   * Gestion de l’audience: `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Données contextuelles Analytics/Paramètre: `a.Resolution`
   * Gestion de l’audience: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >The Days since last upgrade, Launches since last upgrade, and the Carrier Name dimensions are not automatically stored in an Analytics variable. ****** You must create a processing rule to copy the values to an Analytics variable for reporting.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

The following metrics and dimensions are captured in mobile solution variables by the listed method.

### Mesures

* **Durée totale de l’action**

   Renseigné par les méthodes trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Renseigné par les méthodes trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Renseignée par les méthodes trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### Dimensions

* **Lieu (jusqu’à 10 km)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management trait:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes trackLocation.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Populated by `trackLocation` methods.

   * Paramètre Données contextuelles Analytics/Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil est dans un point ciblé défini.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil est dans un point ciblé défini.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseignée par les méthodes trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **Code de suivi**

   Renseigné par l’acquisition des applications mobiles. Généré automatiquement par Adobe Mobile Services.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nom de la campagne, également stocké dans la variable de campagne. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **Contenu de campagne**

   Le nom ou l’identifiant du contenu qui a affiché le lien. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **Support de campagne**

   Support marketing, une bannière ou un courrier électronique par exemple. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **Source de campagne**

   Référent original, comme la newsletter ou les médias sociaux. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **Termes de campagne**

   Mots-clés ou autres termes payés dont vous souhaitez effectuer le suivi avec cette acquisition. Renseigné par l’acquisition des applications mobiles.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`

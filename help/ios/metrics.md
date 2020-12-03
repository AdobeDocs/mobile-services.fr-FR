---
description: Les tables suivantes répertorient les mesures et les dimensions pouvant être mesurées automatiquement par la bibliothèque mobile une fois la mise en œuvre du cycle de vie terminée.
seo-description: Les tables suivantes répertorient les mesures et les dimensions pouvant être mesurées automatiquement par la bibliothèque mobile une fois la mise en œuvre du cycle de vie terminée.
seo-title: Mesures de cycle de vie
solution: Experience Cloud,Analytics
title: Mesures de cycle de vie
topic: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 100%

---


# Mesures de cycle de vie {#lifecycle-metrics}

Voici les mesures et les dimensions pouvant être mesurées automatiquement par la bibliothèque mobile une fois la mise en œuvre du cycle de vie terminée.

## Nouvelle mise à jour du SDK Adobe Experience Platform Mobile

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à [Experience Platform Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Mesures et dimensions de cycle de vie {#section_78F036C4296F4BA3A47C2044F79C86C1}

Une fois les mesures de cycle de vie configurées, elles sont envoyées dans les paramètres de données contextuelles d’Analytics, dans les paramètres de Target avec chaque appel de mbox, et transmises en tant que signal à Audience Manager. Analytics et Target utilisent le même format, tandis qu’Audience Manager utilise un préfixe différent pour chaque mesure.

Pour Analytics, les données contextuelles envoyées avec chaque appel de suivi de cycle de vie sont automatiquement capturées et consignées à l’aide de la mesure ou de la dimension répertoriée dans la première colonne.

>[!TIP]
>
>Les exceptions sont fournies dans la description.

### Mesures

* **Premiers lancements**

   Déclenchée lors de la première exécution après l’installation ou la réinstallation.

   * Données contextuelles Analytics/Paramètre Target : `a.InstallEvent`
   * Signal d’Audience Manager : `c_a_InstallEvent`

* **Mises à niveau**

   Déclenché lors de la première exécution après mise à niveau ou dès que le numéro de version change.

   * Données contextuelles Analytics/Paramètre Target : `a.UpgradeEvent`
   * Signal d’Audience Manager : `c_a_UpgradeEvent`

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   * Données contextuelles Analytics/Paramètre Target : `a.DailyEngUserEvent`
   * Signal d’Audience Manager : `c_a_DailyEngUserEvent`

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée un mois spécifique.

   * Données contextuelles Analytics/Paramètre Target : `a.MonthlyEngUserEvent`
   * Signal d’Audience Manager : `c_a_MonthlyEngUserEvent`

* **Lancements**

   Déclenché à chaque exécution, y compris les blocages et les installations. Également déclenché lorsque l’application reprend en arrière-plan après le dépassement du délai d’expiration de la session de cycle de vie.

   * Données contextuelles Analytics/Paramètre Target : `a.LaunchEvent`
   * Signal d’Audience Manager : `c_a_LaunchEvent`

* **Blocages**

   Déclenché lorsque l’application n’est pas mise en arrière-plan avant sa fermeture. L’événement est envoyé au redémarrage de l’application après son plantage.  La création de rapports de blocage d’Adobe Mobile n’implémente pas un gestionnaire d’exceptions non interceptées global.

   * Données contextuelles Analytics/Paramètre Target : `a.CrashEvent`
   * Signal d’Audience Manager : `c_a_CrashEvent`

* **Durée de la session précédente**

   Mesure la durée en secondes d’une session précédente en fonction de la durée pendant laquelle l’application est restée ouverte et en premier plan.

   * Données contextuelles Analytics/Paramètre Target : `a.PrevSessionLength`
   * Signal d’Audience Manager : `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Les mesures *Utilisateurs actifs par jour* et *Utilisateurs actifs par mois* ne sont pas automatiquement stockées dans une mesure Analytics. Pour capturer ces mesures, vous devez créer une règle de traitement définissant un événement personnalisé.

#### Dimensions

* **La date d’installation**

   Date du premier lancement après installation.  Le format de date est `MM/DD/YYYY`.

   * Données contextuelles Analytics/Paramètre : `a.InstallDate`
   * Gestion de l’audience : `c_a_InstallDate`

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant `[AppName] [BundleVersion]`. Par exemple : `myapp 1.1`.

   * Données contextuelles Analytics/Paramètre : `a.AppID`
   * Gestion de l’audience : `c_a_AppID`

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

   * Données contextuelles Analytics/Paramètre : `a.Launches`
   * Gestion de l’audience : `c_a_Launches`

* **Nombre de jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

   * Données contextuelles Analytics/Paramètre : `a.DaysSinceFirstUse`
   * Gestion de l’audience : `c_a_DaysSinceFirstUse`

* **Nombre de jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière exécution.

   * Données contextuelles Analytics/Paramètre : `a.DaysSinceLastUse`
   * Gestion de l’audience : `c_a_DaysSinceLastUse`

* **Heure du jour**

   Mesure l’heure de lancement de l’application suivant le format numérique de 24 heures. Utilisée pour le découpage temporel afin de déterminer les heures hautes d’utilisation.

   * Données contextuelles Analytics/Paramètre : `a.HourOfDay`
   * Gestion de l’audience : `c_a_HourOfDay`

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

   * Données contextuelles Analytics/Paramètre : `a.DayOfWeek`
   * Gestion de l’audience : `c_a_DayOfWeek`

* **Version du système d’exploitation**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   * Données contextuelles Analytics/Paramètre : `a.OSVersion`
   * Gestion de l’audience : `c_a_OSVersion|OS version`

* **Nombre de jours depuis la dernière mise à niveau**

   Nombre de jours depuis la dernière mise à niveau.

   * Données contextuelles Analytics/Paramètre : `a.DaysSinceLastUpgrade`
   * Gestion de l’audience : `c_a_DaysSinceLastUpgrade`

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   * Données contextuelles Analytics/Paramètre : `a.LaunchesSinceUpgrade`
   * Gestion de l’audience : `c_a_LaunchesSinceUpgrade`

* **Nom de l’appareil**

   Stocke le nom de l’appareil.  Chaîne de deux chiffres séparés par une virgule qui identifie l’appareil iOS. Le premier chiffre représente généralement la génération de l’appareil, et le second les différents membres de la famille d’appareils. Pour obtenir la liste des noms d’appareils courants, reportez-vous à    Versions des appareils iOS.

   * Données contextuelles Analytics/Paramètre : `a.DeviceName`
   * Gestion de l’audience : `c_a_DeviceName`

* **Nom de l’opérateur**

   Stocke le nom du fournisseur de services mobiles transmis par l’appareil.

   * Données contextuelles Analytics/Paramètre : `a.CarrierName`
   * Gestion de l’audience : `c_a_CarrierName`

* **Résolution**

   Largeur x Hauteur en pixels.

   * Données contextuelles Analytics/Paramètre : `a.Resolution`
   * Gestion de l’audience : `c_a_Resolution`
   >[!IMPORTANT]
   >
   >Les dimensions *Jours depuis la dernière mise à niveau*, *Lancements depuis la dernière mise à niveau*, et *Nom de l’opérateur* ne sont pas automatiquement stockées dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier ces valeurs dans une variable Analytics.


## Mesures et dimensions mobiles supplémentaires {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Les mesures et dimensions suivantes sont capturées dans les variables de solution mobile par la méthode répertoriée.

### Mesures

* **Durée totale de l’action**

   Renseigné par les méthodes trackTimedAction.

   * Données contextuelles Analytics/Paramètre Target : `a.action.time.total`
   * Caractéristique de la gestion de l’audience : `c_a_action_time_total`

* **Durée de l’action dans l’application**

   Renseigné par les méthodes trackTimedAction.

   * Données contextuelles Analytics/Paramètre Target : `a.action.time.inapp`
   * Caractéristique de la gestion de l’audience : `c_a_action_time_inapp`

* **Valeur de durée de vie (événement)**

   Renseignée par les méthodes trackLifetimeValue.

   * Données contextuelles Analytics/Paramètre Target : `a.ltv.amount`
   * Caractéristique de la gestion de l’audience : `c_a_ltv_amount`


### Dimensions

* **Lieu (jusqu’à 10 km)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Lieu (jusqu’à 100 m)**

   Renseigné par les méthodes trackLocation.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Lieu (jusqu’à 1 m)**

   Renseigné par les méthodes `trackLocation`.

   * Données contextuelles Analytics/Paramètre Target :

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caractéristique de la gestion de l’audience :

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nom du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil est dans un point ciblé défini.

   * Données contextuelles Analytics/Paramètre Target : `a.loc.poi`
   * Caractéristique de la gestion de l’audience : `c_a_loc_poi`

* **Distance jusqu’au centre du point ciblé**

   Renseigné par les méthodes trackLocation lorsque l’appareil est dans un point ciblé défini.

   * Données contextuelles Analytics/Paramètre Target : `a.loc.dist`
   * Caractéristique de la gestion de l’audience : `c_a_loc_dist`

* **Valeur de durée de vie (variable de conversion)**

   Renseignée par les méthodes trackLifetimeValue.

   * Données contextuelles Analytics/Paramètre Target : `a.ltv.amount`
   * Caractéristique de la gestion de l’audience : `c_a_ltv_amount`

* **Code de suivi**

   Renseigné par l’acquisition des applications mobiles. Généré automatiquement par Adobe Mobile Services.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.trackingcode`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nom de la campagne, également stocké dans la variable de campagne. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.name`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_name`

* **Contenu de campagne**

   Le nom ou l’identifiant du contenu qui a affiché le lien. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.content`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_content`

* **Support de campagne**

   Support marketing, une bannière ou un courrier électronique par exemple. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.medium`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_medium`

* **Source de campagne**

   Référent original, comme la newsletter ou les médias sociaux. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.source`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_source`

* **Termes de campagne**

   Mots-clés ou autres termes payés dont vous souhaitez effectuer le suivi avec cette acquisition. Renseigné par l’acquisition des applications mobiles.

   * Données contextuelles Analytics/Paramètre Target : `a.referrer.campaign.term`
   * Caractéristique de la gestion de l’audience : `c_a_referrer_campaign_term`

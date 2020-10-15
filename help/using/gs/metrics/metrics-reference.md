---
description: Voici les informations de référence sur les dimensions et les mesures mobiles par défaut.
keywords: mobile
seo-description: Voici les informations de référence sur les dimensions et les mesures mobiles par défaut.
seo-title: Référence sur les dimensions et les mesures mobiles
solution: Experience Cloud,Analytics
title: Référence sur les dimensions et les mesures mobiles
topic: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '637'
ht-degree: 100%

---


# Référence sur les dimensions et les mesures mobiles {#mobile-metrics-and-dimensions-reference}

Ces informations vous aident à mieux comprendre les mesures et dimensions mobiles par défaut.

>[!TIP]
>
>Les droits d’accès aux dimensions et aux mesures configurés dans Adobe Analytics s’appliquent à Mobile Services. Lorsque vous essayez d’exécuter un rapport sans les autorisations appropriées, une erreur se produit.

## Mesures {#section_6704C815147D44AF96151D626BEB813C}

Voici la liste des mesures mobiles par défaut :

* **Premiers lancements**

   Déclenché lors de la première exécution après l’installation ou la réinstallation.

* **Mises à niveau**

   Déclenché lors de la première exécution après la mise à niveau ou dès que le numéro de version change.

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!TIP]
   >
   >L’événement Utilisateurs actifs/jour n’est pas enregistré automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée pendant un mois.

   >[!TIP]
   >L’événement Utilisateurs actifs par mois n’est pas enregistré automatiquement dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

* **Lancements**

   Déclenché à l’exécution (qui ne fait pas suite à une installation ou à une mise à niveau). Cet événement se déclenche également lorsque l’application est mise en premier plan. Par défaut, un nouveau lancement se déclenche lorsque l’application est mise en arrière-plan pendant cinq minutes ou plus. La durée de mise en arrière-plan écoulée avant le déclenchement d’un nouveau lancement peut être configurée dans les **[!UICONTROL Options du SDK Analytics]** sur la page Gestion des paramètres de l’application. Pour plus d’informations, voir la ligne *Délai d’expiration de session (secondes)* dans [Configuration des options SDK Analytics](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >En raison du mode de calcul des visites dans [!UICONTROL Adobe Analytics] et des lancements d’applications mobiles dans [!UICONTROL Adobe Mobile Services], il est possible d’obtenir des résultats différents dans les rapports. Pour plus d’informations, voir [Comparaison des visites et des lancements d’applications mobiles](https://helpx.adobe.com/fr/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Blocages**

   Déclenché lorsque l’application ne se ferme pas correctement. Cet événement est envoyé lorsque l’application débute après un blocage.

   >[!TIP]
   >L’application est considérée comme bloquée si la sortie n’est pas appelée.

* **Durée totale de la session**

   Total agrégé de la durée de la session.

## Dimensions {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Voici la liste des mesures mobiles par défaut :

* **La date d’installation**

   Date du premier lancement après installation. La date est au format *MM/JJ/AAAA*.

* **ID d’application**

   Stocke le nom et la version de l’application au format suivant : `[AppName] [BundleVersion]` Par exemple : `myapp 1.1`.

* **Numéro de lancement**

   Nombre de fois où l’application a été lancée ou mise en premier plan.

* **Jours depuis la première utilisation**

   Nombre de jours depuis la première exécution.

* **Jours depuis la dernière utilisation**

   Nombre de jours depuis la dernière utilisation.

* **Heure du jour**

   Mesure l’heure à laquelle l’application a été lancée au format numérique de 24 heures. Cette dimension est également utilisée pour le découpage temporel afin de déterminer les heures hautes d’utilisation.

* **Jour de la semaine**

   Numéro du jour de la semaine où l’application a été lancée.

* **Système d’exploitation**

   Système d’exploitation de l’appareil.

* **Version du système d’exploitation**

   Version du système d’exploitation.

* **Jours depuis la dernière mise à niveau**

   Nombre de jours depuis que le numéro de version de l’application a changé.

   >[!TIP]
   >
   >La mesure du nombre de jours depuis la dernière mise à niveau n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!TIP]
   >
   >La mesure du nombre de lancements depuis la dernière mise à niveau n’est pas enregistrée automatiquement dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

* **Nom de l’appareil**

   Stocke le nom de l’appareil. Sous iOS, une chaîne de deux chiffres séparée par une virgule identifie l’appareil iOS. Le premier chiffre représente généralement la génération de l’appareil, le second les différents membres de la famille d’appareils. Pour obtenir la liste complète des noms d’appareils courants, voir [Versions des appareils iOS](/help/ios/reference/device-versions.md).

* **Nom de l’opérateur**

   Stocke le nom de l’opérateur de téléphonie mobile.

* **Résolution**

   Largeur et hauteur en pixels.

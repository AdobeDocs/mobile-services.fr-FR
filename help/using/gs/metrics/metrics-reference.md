---
description: Voici les informations de référence sur les dimensions et les mesures mobiles par défaut.
keywords: mobile
seo-description: Voici les informations de référence sur les dimensions et les mesures mobiles par défaut.
seo-title: Référence sur les dimensions et les mesures mobiles
solution: Marketing Cloud, Analytics
title: Référence sur les dimensions et les mesures mobiles
topic: Mesures
uuid: 96170 ae 7-8553-4 f 3 e-ae 01-65 e 5 b 664 adf 4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

Ces informations vous aident à mieux comprendre les mesures et dimensions mobiles par défaut.

>[!TIP]
>
>Les autorisations de dimension et de mesure définies dans Adobe Analytics s'appliquent aux services mobiles. Lorsque vous essayez d'exécuter un rapport sans les autorisations adéquates, une erreur se produit.

## Mesures {#section_6704C815147D44AF96151D626BEB813C}

Voici la liste des mesures mobiles par défaut :

* **Premiers lancements**

   Déclenché lors de la première exécution après l’installation ou la réinstallation.

* **Mises à niveau**

   Déclenché lors de la première exécution après la mise à niveau ou dès que le numéro de version change.

* **Utilisateurs actifs/jour**

   Déclenché lorsque l’application est utilisée un jour spécifique.

   >[!TIP]
   >L'événement Utilisateurs actifs quotidiens n'est pas automatiquement stocké dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

* **Utilisateurs actifs par mois**

   Déclenché lorsque l’application est utilisée pendant un mois.

   >[!TIP]
   >L'événement Utilisateurs actifs mensuels n'est pas automatiquement stocké dans une mesure Analytics. Pour capturer cette mesure, vous devez créer une règle de traitement définissant un événement personnalisé.

* **Lancements**

   Déclenché à l’exécution (qui ne fait pas suite à une installation ou à une mise à niveau). Cet événement se déclenche également lorsque l’application est mise en premier plan. Par défaut, un nouveau lancement se déclenche lorsque l’application est mise en arrière-plan pendant cinq minutes ou plus. The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. Pour plus d'informations, reportez-vous à la ligne Délai *d'expiration de session (secondes)* dans [Configuration des options SDK Analytics](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. Pour plus d’informations, voir [Comparaison des visites et des lancements d’applications mobiles](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Blocages**

   Déclenché lorsque l’application ne se ferme pas correctement. Cet événement est envoyé au démarrage de l’application après un blocage.

   >[!TIP]
   >L'application est considérée comme bloquée si la fermeture n'est pas appelée.

* **Durée totale de la session**

   Total agrégé de la durée de la session.

## Dimensions {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Voici la liste des dimensions mobiles par défaut :

* **la date d’installation**

   Date du premier lancement après installation. La date est au format *MM/JJ/AAAA*.

* **ID d’application**

   Stores the Application name and version in the following format: `[AppName] [BundleVersion]`. Par exemple : `myapp 1.1`.

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
   >Les jours depuis la dernière mise à niveau ne sont pas automatiquement stockés dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

* **Lancements depuis la dernière mise à niveau**

   Nombre de lancements depuis que le numéro de version de l’application a changé.

   >[!TIP]
   >
   >Les lancements depuis la dernière mise à niveau ne sont pas automatiquement stockés dans une variable Analytics. Pour générer des rapports, vous devez créer une règle de traitement permettant de copier cette valeur dans une variable Analytics.

* **Nom de l’appareil**

   Stocke le nom de l’appareil. Sous ios, une chaîne à deux chiffres séparée par des virgules identifie le périphérique ios. Le premier chiffre représente la génération de l'appareil et les autres versions de la famille de périphériques. Pour obtenir la liste complète des noms d’appareils courants, voir [Versions des appareils iOS](/help/ios/reference/device-versions.md).

* **Nom de l’opérateur**

   Stocke le nom de l’opérateur de téléphonie mobile.

* **Résolution**

   Largeur et hauteur en pixels.

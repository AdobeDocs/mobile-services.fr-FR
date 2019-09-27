---
description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Marketing Cloud,Analytics
title: Notes de mise à jour
topic: Développeur et mise en œuvre
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notes de mise à jour {#release-notes}

Here is the release notes, known issues, and hot fix information for Android SDK 4.x for Experience Cloud Solutions:

**September 20, 2019: Version 4.17.10**

* General: Fixed locale string generation for some regions on Android API level 21 or newer.

**July 18, 2019: Version 4.17.8**

* Adobe Target : Toutes les requêtes incluent désormais le client et l’ID de session dans les paramètres de requête d’URL.
* Messagerie In-App : correction d’un problème en raison duquel les applications Android se bloquaient lorsqu’un message était déclenché avec une URL de taux de clics vide.
* Service d’identification des visiteurs : les API `Visitor.appendToURL` et `Visitor.getUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**June 6, 2019: Version 4.17.7**

* Général - Les appels de mise en réseau sur les niveaux d'API Android inférieurs à 20 utilisent désormais TLS 1.1 ou TLS 1.2.
* Analytics - Ajout de l’état d’inclusion Push aux données de cycle de vie lorsque les notifications Push sont activées.

**24 mai 2019 : Version 4.17.6**

* service d’identification des visiteurs - Le
   `setPushIdentifier` L’appel d’API envoie désormais un appel asynchrone au service d’identification des visiteurs chaque fois qu’il est appelé.

* Service d’identification des visiteurs - Augmentation du délai d’attente de la connexion et des lectures de 2 à 5 secondes.


Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

---
description: Notes de mise à jour et problèmes connus pour les SDK iOS 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus pour les SDK iOS 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Experience Cloud,Analytics
title: Notes de mise à jour
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 6c8020b88d22489f86853274d29dbceee504aa06
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 89%

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations sur les correctifs pour les SDK iOS 4.x pour les solutions Experience Cloud :

**4 novembre 2020 : Version 4.20.0**

* Service d’identification des visiteurs - Paramètre d’état device_consentement Ajouté lorsque setAdvertisingIdentifier est appelé une fois le suivi des publicités activé/désactivé.
* Analytics - Correction d’un bogue qui retardait l’envoi des accès Analytics lors d’une installation lorsque iAd.framework était lié et que le suivi des publicités limité était activé sur le périphérique.

**16 juillet 2020 : Version 4.19.3**

* Général : Correction d’un bug qui empêchait le traitement correct des URL de lien profond avec plusieurs signes égal dans le paramètre de requête.

**24 mars 2020 : Version 4.19.2**

* Général : correction de certaines failles dans le code Target.

**12 mars 2020 : Version 4.19.1**

* Général : Résolution d’un blocage potentiel lorsque des énumérations Swift sont incluses dans les données contextuelles des appels de suivi.
* Target : L’ID de session Target sera désormais ajouté comme paramètre de données contextuelles ‘a.target.sessionId’ dans l’accès interne Analytics for Target envoyé à Adobe Analytics.

**4 février 2020 : version 4.19.0**

* Cycle de vie : Ajout d’une nouvelle API, pauseCollectingLifecycleData, afin d’atténuer les données de durée de session anormale signalées par certains appareils iOS anciens.

**8 novembre 2019 : version 4.18.9**

* Dans la messagerie intégrée (in-app) : correction d’un bogue en raison duquel les images mises en cache ou regroupées ne pouvaient pas être chargées dans les messages en plein écran.

**20 septembre 2019 : Version 4.18.8**

* Messagerie in-app :

   * Sur les appareils exécutant iOS 10 ou une version plus récente, le cadre `UserNotifications` est maintenant utilisé pour planifier des notifications locales pour les applications liées à `UserNotifications.framework`.
   * Les messages en plein écran utilisent maintenant WKWebViews de `WebKit.framework`, qui doit être lié dans votre projet Xcode.
   * Correction d’un bogue en raison duquel la charge utile des clics publicitaires ne pouvait pas être utilisée comme caractéristiques pour la messagerie intégrée (in-app).
   * Correction d’un problème de blocage.

* Général : Correction d’un bogue en raison duquel les données du SDK étaient synchronisées avec l’application watchOS couplée à chaque appel Analytics.

**2 août 2019 : Version 4.18.7**

* Annulation d’une modification introduite dans la version 4.18.6, qui, dans certains environnements, provoquait un blocage sur les périphériques exécutant une version iOS antérieure à 11.0.

* Adobe Target : Ajout de la propriété `requestLocationParameters` dans `ADBTargetRequestObject`, ce qui permet l’envoi de la valeur impressionID avec les requêtes Target.

**18 juillet 2019 : Version 4.18.6**

* Adobe Target : toutes les demandes comprennent désormais le client et `sessionId` dans les paramètres de requête d’URL.
* Adobe Target : correction d’une fuite de mémoire.
* Service d’identification des visiteurs : les API `visitorAppendToURL` et `visitorGetUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**5 juin 2019 : Version 4.18.5**

* Analytics : Ajoutez l’état d’inclusion push aux données de cycle de vie lorsque les notifications push sont activées.

**24 mai 2019 : Version 4.18.4**

* Service d’identification des visiteurs : Augmentation du délai d’attente des retours pour la variable
   `visitorGetUrlVariablesAsync` API à 30 secondes.

* Service d’identification des visiteurs : l’appel API `setPushIdentifier` envoie désormais un appel de synchronisation au service d’identification des visiteurs à chaque appel.

Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://docs.adobe.com/content/help/fr-FR/release-notes/experience-cloud/current.html).

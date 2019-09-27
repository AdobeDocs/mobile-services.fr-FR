---
description: Notes de mise à jour et problèmes connus des SDK iOS 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus des SDK iOS 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Marketing Cloud,Analytics
title: Notes de mise à jour
topic: Développeur et mise en œuvre
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations sur les correctifs pour les SDK iOS 4.x pour les solutions Experience Cloud :

**20 septembre 2019 : Version 4.18.8**

* Messagerie in-app :

   * Sur les périphériques exécutant iOS 10 ou une version plus récente, la `UserNotifications` structure est désormais utilisée pour programmer des notifications locales pour les applications liées à `UserNotifications.framework`.
   * Les messages en plein écran utilisent désormais WKWebViews de `WebKit.framework`, qui doit être lié dans votre projet Xcode.
   * Correction d’un bogue en raison duquel la charge utile de clic publicitaire Push ne pouvait pas être utilisée comme caractéristiques pour la messagerie in-app.
   * Correction d’un problème de plantage.

* Général - Correction d’un bogue en raison duquel les données du SDK étaient synchronisées avec l’application watchOS associée pour chaque appel Analytics.

**2 août 2019 : Version 4.18.7**

* Reverted a change that was introduced in version 4.18.6 which, in some environments, caused a crash on devices that were running an iOS version older than 11.0.

* Adobe Target: Added the  property in , which enables the impressionId to be sent with Target requests.`requestLocationParameters``ADBTargetRequestObject`

**July 18, 2019: Version 4.18.6**

* Adobe Target : toutes les demandes comprennent désormais le client et `sessionId` dans les paramètres de requête d’URL.
* Adobe Target : correction d’une fuite de mémoire.
* Service d’identification des visiteurs : les API `visitorAppendToURL` et `visitorGetUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**5 juin 2019 : Version 4.18.5**

* Analytics - Append push opt-in status to Lifecycle data when push notifications are enabled.

**May 24, 2019: Version 4.18.4**

* Visitor ID Service - Increased the return timeout for the
   `visitorGetUrlVariablesAsync` API to 30 seconds.

* Visitor ID Service - The  API call now sends a sync call to the Visitor ID Service every time it is called.`setPushIdentifier`

Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

---
description: Notes de mise à jour et problèmes connus pour les SDK Android 4.x pour les solutions Experience Cloud.
solution: Experience Cloud,Analytics
title: Notes de mise à jour
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations sur les correctifs pour le SDK Android 4.x pour les solutions Experience Cloud :

## 3 avril 2020 : 4.18.2

* Messagerie in-app : pour des raisons de sécurité, les WebViews créés par le SDK définissent désormais la propriété `setAllowFileAccess` sur `false`.

## 12 mars 2020 : 4.18.1

* Target : l’ID de session Target est désormais ajouté en tant que paramètre de données contextuelles `a.target.sessionId` dans l’accès Analytics-for-Target interne envoyé à Adobe Analytics.

## 16 janvier 2020 : 4.18.0

* Acquisition : ajout d’une nouvelle API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, afin de prendre en charge les API Install Referrer de Google Play.

   Pour plus d’informations sur les API Install Referrer, voir [Still Using InstallBroadcast? Switch to the Play Referrer API by March 1, 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) (article en anglais).

## 20 septembre 2019 : Version 4.17.10

* Général : Correction de la génération de chaînes de paramètres régionaux pour certaines régions sur l’API Android de niveau 21 ou plus récent.

## 18 juillet 2019 : Version 4.17.8

* Adobe Target : toutes les demandes comprennent désormais le client et sessionId dans les paramètres de requête d’URL.
* Messagerie in-app : Correction d’un problème en raison duquel les applications Android se bloquaient lorsqu’un message était déclenché avec une URL de clic publicitaire vide.
* Service d’identification des visiteurs : les API `Visitor.appendToURL` et `Visitor.getUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

## 6 juin 2019 : Version 4.17.7

* Général - Les appels de mise en réseau sur les niveaux d’API Android inférieurs à 20 utilisent désormais TLS 1.1 ou TLS 1.2.
* Analytics - Ajout de l’état d’inclusion Push aux données de cycle de vie lorsque les notifications Push sont activées.

## 24 mai 2019 : Version 4.17.6

* service d’identification des visiteurs : l’appel de l’API `setPushIdentifier` envoie désormais un appel de synchronisation au service d’identification des visiteurs à chaque appel.
* Service d’identification des visiteurs - Augmentation du délai d’attente de la connexion et des lectures de 2 à 5 secondes.

Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr).

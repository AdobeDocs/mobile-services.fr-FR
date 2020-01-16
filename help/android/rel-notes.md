---
description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Marketing Cloud,Analytics
title: Notes de mise à jour
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 712a1107b317f02216e4df8d75fddda67a6f1feb

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations sur les correctifs pour le SDK Android 4.x pour les solutions Experience Cloud :

**16 janvier 2020 : 4.18.0**

* Acquisition : ajout d’une nouvelle API `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, pour la prise en charge des API de référents d’installation de Google Play.

   Pour plus d’informations sur l’installation des API de référents, voir [Toujours utiliser InstallBroadcast ? Passez à l’API de référent de lecture d’ici le 1er mars 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) .

**20 septembre 2019 : Version 4.17.10**

* Général : Correction de la génération de chaînes de paramètres régionaux pour certaines régions sur l’API Android de niveau 21 ou plus récent.

**18 juillet 2019 : Version 4.17.8**

* Adobe Target : toutes les demandes comprennent désormais le client et sessionId dans les paramètres de requête d’URL.
* Messagerie In-App : correction d’un problème en raison duquel les applications Android se bloquaient lorsqu’un message était déclenché avec une URL de taux de clics vide.
* Service d’identification des visiteurs : les API `Visitor.appendToURL` et `Visitor.getUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**6 juin 2019 : Version 4.17.7**

* Général - Les appels de mise en réseau sur les niveaux d’API Android inférieurs à 20 utilisent désormais TLS 1.1 ou TLS 1.2.
* Analytics - Ajout de l’état d’inclusion Push aux données de cycle de vie lorsque les notifications Push sont activées.

**24 mai 2019 : Version 4.17.6**

* service d’identification des visiteurs -
   L’appel d’API `setPushIdentifier` envoie désormais un appel asynchrone au service d’identification des visiteurs chaque fois qu’il est appelé.

* Service d’identification des visiteurs - Augmentation du délai d’attente de la connexion et des lectures de 2 à 5 secondes.


Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

---
description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus du SDK Android 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Marketing Cloud,Analytics
title: Notes de mise à jour
topic: Développeur et mise en œuvre
uuid: 16 bb 4 de 8-a 216-47 a 8-928 c -0 b 1 e 1421 adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations de correctif pour Android SDK 4. x pour solutions Experience Cloud :

**2 août 2019 : Version 4.17.9**

* Service d'identification des visiteurs : Correction de `StrictMode` la violation lors de l'appel de syncidentifiers.

   Cette violation était due à la lecture des préférences partagées sur le thread principal.

* Adobe Target : Ajout de `requestLocationParameters` l'attribut dans `TargetRequestObject`, qui permet l'envoi de l'impressionid avec les requêtes Target.

**18 juillet 2019 : Version 4.17.8**

* Adobe Target : Toutes les requêtes incluent désormais le client et le paramètre sessionid dans les paramètres de requête d'URL.
* Messagerie In-App : correction d’un problème en raison duquel les applications Android se bloquaient lorsqu’un message était déclenché avec une URL de taux de clics vide.
* Service d’identification des visiteurs : les API `Visitor.appendToURL` et `Visitor.getUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**6 juin 2019 : Version 4.17.7**

* Général - Les appels réseau sur les niveaux d'API Android inférieurs à 20 utilisent désormais TLS 1.1 ou TLS 1.2.
* Analytics : ajout de l'état de souscription Push aux données du cycle de vie lorsque les notifications Push sont activées.

**24 mai 2019 : Version 4.17.6**

* service d'identification des visiteurs - le
   `setPushIdentifier` L'appel API envoie désormais un
appel de synchronisation au service d'identification des visiteurs chaque fois qu'il est appelé.

* Service d'identification des visiteurs - Augmentation des délais de connexion et des délais de lecture de
2 secondes à 5 secondes.


Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

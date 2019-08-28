---
description: Notes de mise à jour et problèmes connus des SDK iOS 4.x pour les solutions Experience Cloud.
seo-description: Notes de mise à jour et problèmes connus des SDK iOS 4.x pour les solutions Experience Cloud.
seo-title: Notes de mise à jour
solution: Marketing Cloud,Analytics
title: Notes de mise à jour
topic: Développeur et mise en œuvre
uuid: e 1613 dc 5-02 a 4-43 a 7-997 a -29 b 4 de 98 b 4 d 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# Notes de mise à jour {#release-notes}

Voici les notes de mise à jour, les problèmes connus et les informations de correctif pour les SDK ios 4. x pour les solutions Experience Cloud :

**2 août 2019 : Version 4.18.7**

* Restauration d'une modification introduite dans la version 4.18.6 qui, dans certains environnements, provoquait un blocage sur les périphériques exécutant une version ios antérieure à 11.0.

* Adobe Target : Ajout de `requestLocationParameters` la propriété dans `ADBTargetRequestObject`, qui permet l'envoi de l'impressionid avec les requêtes Target.

**18 juillet 2019 : Version 4.18.6**

* Adobe Target : toutes les demandes comprennent désormais le client et `sessionId` dans les paramètres de requête d’URL.
* Adobe Target : correction d’une fuite de mémoire.
* Service d’identification des visiteurs : les API `visitorAppendToURL` et `visitorGetUrlVariablesAsync` ne codent plus deux fois leurs valeurs renvoyées.

   Le double codage entraînait le marquage des valeurs renvoyées de ces API par certaines révisions de sécurité.

**5 juin 2019 : Version 4.18.5**

* Analytics : ajout de l'état de souscription Push aux données du cycle de vie lorsque les notifications Push sont activées.

**24 mai 2019 : Version 4.18.4**

* Service d'identification des visiteurs - augmentation du délai d'attente de retour pour la variable
   `visitorGetUrlVariablesAsync` API à 30 secondes.

* Service d'identification des visiteurs : l'appel `setPushIdentifier` de l'API envoie désormais un appel de synchronisation au service d'identification des visiteurs chaque fois qu'il est appelé.

Pour plus d’informations sur les notes de mise à jour des versions actuelles et antérieures de l’ensemble des solutions, voir les [Notes de mise à jour d’Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

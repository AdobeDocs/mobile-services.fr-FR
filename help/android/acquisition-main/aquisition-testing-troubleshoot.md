---
description: Les informations suivantes vous aident à résoudre les problèmes liés aux tests d'acquisition.
keywords: android ; Acquisition ; test
seo-description: Les informations suivantes vous aident à résoudre les problèmes liés aux tests d'acquisition.
seo-title: Dépannage des tests d'acquisition
solution: Marketing Cloud, Analytics
title: Dépannage des tests d'acquisition
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Dépannage des tests d'acquisition {#aquistion-testing-troubleshooting}

Voici quelques problèmes que vous pouvez rencontrer lors du test d'acquisition et de quelques solutions possibles :

* S'il n'est pas spécifié autrement, le fichier adbmobileconfig. json doit être placé dans le dossier assets.

* Le nom est sensible à la casse. N'indiquez donc pas de nom en minuscules.

   Vous devez vérifier que `Config.setContext(this.getApplicationContext())` l'appel est effectué à partir de l'activité principale. Pour plus d'informations, voir [Méthodes de configuration](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Il manque quelques autorisations utilisateur dans le fichier AndroidManifest.xml fourni, ces dernières sont requises pour envoyer des données et enregistrer les appels de suivi hors ligne :

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Dans votre configuration, si le délai d'expiration du référent est défini `referrerTimeout: 5`sur, cela signifie que vous devez envoyer l'intention d'installation dans un délai de 5 secondes après avoir installé et lancé pour la première fois les informations de référent ajoutées à l'accès à l'installation.

   Pour des tests manuels, augmentez le `referrerTimeout` délai de 10 à 15 secondes afin qu'il y ait suffisamment de temps pour envoyer les informations du référent avant le traitement de l'accès à l'installation.

* Il est important d'exécuter toutes les étapes de [test de l'acquisition](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) des liens marketing dans l'ordre et de s'assurer que vous exécutez `adb` shell puis :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Vous devez exécuter ces deux commandes indépendamment pour traiter correctement l'intention du référent. Sinon, `adb` double-cliquez sur les informations du référent et les données reçues par le destinataire de la diffusion seront incomplètes.

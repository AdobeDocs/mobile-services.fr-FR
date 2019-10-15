---
description: Les informations suivantes vous aident à résoudre les problèmes liés aux tests d’acquisition.
keywords: android;Acquisition;test
seo-description: Les informations suivantes vous aident à résoudre les problèmes liés aux tests d’acquisition.
seo-title: Dépannage des tests d’acquisition
solution: Marketing Cloud,Analytics
title: Dépannage des tests d’acquisition
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Dépannage des tests d’acquisition {#aquistion-testing-troubleshooting}

Voici quelques problèmes que vous pouvez rencontrer lors du test d’acquisition et quelques solutions possibles :

* S’il n’est pas spécifié autrement, le fichier ADBMobileConfig.json doit être placé dans le dossier assets.

* Le nom étant sensible à la casse, n’indiquez pas de nom en minuscules.

   Vous devez vous assurer que l’appel `Config.setContext(this.getApplicationContext())` est effectué à partir de l’activité principale. Pour plus d’informations, voir Méthodes [de](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)configuration.

* Il manque quelques autorisations d’utilisateur dans le fichier AndroidManifest.xml fourni. Ces autorisations sont requises pour envoyer des données et enregistrer des appels de suivi hors ligne :

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Dans votre configuration, si le délai d’expiration du référent est défini `referrerTimeout: 5`, cela signifie que vous devez envoyer le mode d’installation dans un délai de 5 secondes après l’installation et le lancement de l’application pour la première fois afin que les informations du référent soient ajoutées à l’accès à l’installation.

   Pour les tests manuels, augmentez le délai `referrerTimeout` à 10-15 secondes, de sorte qu’il y ait suffisamment de temps pour envoyer les informations sur le référent avant le traitement de l’accès à l’installation.

* Il est important d’exécuter toutes les étapes du [test de l’acquisition](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) de liens marketing afin de vous assurer que vous exécutez `adb` shell, puis les étapes suivantes :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Vous devez exécuter ces deux commandes indépendamment pour traiter correctement l’intention du référent.  Dans le cas contraire, `adb` double séquence d’échappement des informations du référent et les données reçues par le récepteur de diffusion seront incomplètes.

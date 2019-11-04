---
description: Les informations suivantes vous aident à dépanner les tests d’Acquisition.
keywords: android;Acquisition;testing
seo-description: Les informations suivantes vous aident à dépanner les tests d’Acquisition.
seo-title: Dépannage des tests d’Acquisition
solution: Experience Cloud,Analytics
title: Dépannage des tests d’Acquisition
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Dépannage des tests d’Acquisition {#aquistion-testing-troubleshooting}

Voici quelques problèmes que vous pouvez rencontrer lors des tests d’Acquisition et quelques solutions possibles :

* Sauf indication contraire, le fichier ADBMobileConfig.json doit être placé dans le dossier assets.

* Le nom étant sensible à la casse, n’indiquez pas de nom en minuscules.

   Vous devez vous assurer que l’appel `Config.setContext(this.getApplicationContext())` est effectué à partir de l’activité principale. Pour plus d’informations, voir [Méthodes de configuration](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/configuration-android/methods.html).

* Il manque quelques autorisations d’utilisateur dans le fichier AndroidManifest.xml fourni. Ces autorisations sont requises pour envoyer des données et enregistrer des appels de suivi hors ligne :

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Dans votre configuration, si le délai d’expiration du référent est défini sur `referrerTimeout: 5`, cela signifie que vous devez envoyer le mode d’installation dans un délai de 5 secondes après l’installation et le lancement de l’application pour la première fois afin que les informations du référent soient ajoutées à l’accès à l’installation.

   Pour les tests manuels, augmentez le `referrerTimeout` pour atteindre 10-15 secondes, de sorte qu’il y ait suffisamment de temps pour envoyer les informations sur le référent avant le traitement de l’accès à l’installation.

* Il est important d’exécuter toutes les étapes de l’[Évaluation de l’acquisition d’un lien marketing](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) afin de vous assurer que vous exécutez le conteneur `adb` puis les étapes suivantes :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Vous devez exécuter ces deux commandes indépendamment pour traiter correctement l’intention du référent.  Dans le cas contraire, `adb` lancera une double séquence d’échappement des informations du référent et les données reçues par le récepteur de diffusion seront incomplètes.

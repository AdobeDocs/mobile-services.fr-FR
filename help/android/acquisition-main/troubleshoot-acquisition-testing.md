---
description: Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’acquisition.
keywords: android;library;mobile;sdk
seo-description: Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’acquisition.
seo-title: Résolution des problèmes liés aux tests d’acquisition
solution: Marketing Cloud,Analytics
title: Résolution des problèmes liés aux tests d’acquisition
topic: Développeur et mise en œuvre
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Résolution des problèmes liés aux tests d’acquisition {#troubleshoot-acquisition-testing}

Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’acquisition.

* S’il n’est pas spécifié autrement, le fichier ADBMobileConfig.json doit être placé dans le `assets` dossier.

   Le nom étant sensible à la casse, n’utilisez pas de lettres majuscules ou minuscules.

* Assurez-vous que `Config.setContext(this.getApplicationContext())` l’appel est effectué à partir de votre activité principale.

   Pour plus d’informations, voir Méthodes [de](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)configuration.

* Assurez-vous que les autorisations requises pour le kit SDK mobile sont présentes dans le `AndroidManifest.xml` fichier :

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si le paramètre `referrerTimeout` est défini sur 5 dans le fichier ADMobileConfig.json, vous devez envoyer le mode d’installation dans un délai de 5 secondes après l’installation et le lancement de l’application pour la première fois afin que les informations du référent soient ajoutées à l’accès à l’installation.

   Pour les tests manuels, nous vous recommandons d’augmenter le délai `referrerTimeout` à 10-15 secondes afin que vous ayez suffisamment de temps pour envoyer les informations sur le référent avant le traitement de l’accès à l’installation.

* Exécutez toutes les étapes du [test de l’acquisition](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) de liens marketing et assurez-vous d’exécuter d’abord la `adb shell` commande, puis les étapes suivantes :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Pour traiter correctement l’intention du référent, vous devez exécuter ces deux commandes indépendamment. Dans le cas contraire, `adb` les informations du référent seront ignorées deux fois et les données reçues par le récepteur seront incomplètes.


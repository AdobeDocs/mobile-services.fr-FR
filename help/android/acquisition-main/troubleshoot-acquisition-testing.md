---
description: Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’Acquisition.
keywords: android;library;mobile;sdk
seo-description: Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’Acquisition.
seo-title: Dépannage des tests d’Acquisition
solution: Experience Cloud,Analytics
title: Dépannage des tests d’Acquisition
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---

# Dépannage des tests d’Acquisition {#troubleshoot-acquisition-testing}

Cette rubrique fournit des informations sur la manière de résoudre les problèmes que vous pourriez rencontrer lors des tests d’Acquisition.

* Sauf indication contraire, le fichier ADBMobileConfig.json doit être placé dans le dossier `assets`.

   Le nom étant sensible à la casse, n’utilisez pas de lettres majuscules ou minuscules.

* Vérifiez que `Config.setContext(this.getApplicationContext())` est appelé depuis votre activité principale.

   Pour plus d’informations, voir [Méthodes de configuration](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/configuration-android/methods.html).

* Vérifiez que les autorisations requises pour le kit SDK Mobile sont présentes dans le fichier `AndroidManifest.xml`.

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si le paramètre `referrerTimeout` est défini sur 5 dans le fichier ADMobileConfig.json, vous devez envoyer l’intention d’installation dans un délai de 5 secondes après l’installation et le lancement de l’application pour la première fois afin que les informations du référent soient ajoutées à l’accès à l’installation.

   Pour les tests manuels, nous vous recommandons d’augmenter le délai `referrerTimeout` à 10-15 secondes afin d’avoir suffisamment de temps pour envoyer les informations du référent avant le traitement de l’accès à l’installation.

* Suivez toutes les étapes de l’[Évaluation de l’acquisition d’un lien marketing](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) et assurez-vous d’exécuter d’abord la commande `adb shell`, puis les étapes suivantes :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Pour traiter correctement l’intention du référent, vous devez exécuter ces deux commandes indépendamment. Sinon `adb` échappera doublement aux informations du référent et les données reçues par le récepteur de diffusion seront incomplètes.

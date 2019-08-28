---
description: Cette rubrique fournit des informations sur la résolution des problèmes que vous pourriez rencontrer lors du test de l'acquisition.
keywords: android ; library ; mobile ; sdk
seo-description: Cette rubrique fournit des informations sur la résolution des problèmes que vous pourriez rencontrer lors du test de l'acquisition.
seo-title: Résolution des problèmes liés aux tests d'acquisition
solution: Marketing Cloud, Analytics
title: Résolution des problèmes liés aux tests d'acquisition
topic: Développeur et mise en œuvre
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Résolution des problèmes liés aux tests d'acquisition {#troubleshoot-acquisition-testing}

Cette rubrique fournit des informations sur la résolution des problèmes que vous pourriez rencontrer lors du test de l'acquisition.

* S'il n'est pas spécifié autrement, le fichier adbmobileconfig. json doit être placé dans `assets` le dossier.

   Le nom est sensible à la casse ; n'utilisez donc pas de lettres majuscules ou minuscules.

* Vérifiez que `Config.setContext(this.getApplicationContext())` l'appel est effectué à partir de votre activité principale.

   Pour plus d'informations, voir [Méthodes de configuration](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Assurez-vous que les autorisations requises pour le kit SDK Mobile sont présentes dans `AndroidManifest.xml` le fichier :

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si le `referrerTimeout` paramètre est défini sur 5 dans le fichier admobileconfig. json, vous devez envoyer l'intention d'installation dans un délai de 5 secondes après avoir installé et lancé pour la première fois les informations de référent ajoutées à l'accès à l'installation.

   Pour des tests manuels, nous vous recommandons d'augmenter `referrerTimeout` le délai de 10 à 15 secondes afin d'avoir suffisamment de temps pour envoyer les informations du référent avant le traitement de l'accès à l'installation.

* Exécutez toutes les étapes de [Test de l'acquisition des liens marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) et assurez-vous d'exécuter la `adb shell` commande d'abord, puis les éléments suivants :

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Pour traiter correctement le mode de référent, vous devez exécuter ces deux commandes indépendamment. Sinon `adb` , double d'échappement les informations du référent et les données reçues par le destinataire de la diffusion seront incomplètes.


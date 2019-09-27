---
description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
keywords: android;library;mobile;sdk
seo-description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
seo-title: Troubleshoot Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshoot Acquisition testing
topic: Développeur et mise en œuvre
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Troubleshoot Acquisition testing {#troubleshoot-acquisition-testing}

This topic provides information about how to troubleshoot issues you might face during Acquisition testing.

* If not otherwise specified, the ADBMobileConfig.json file should be placed in the  folder.`assets`

   The name is case sensitive, so do not use upper or lower case letters.

* Assurez-vous que `Config.setContext(this.getApplicationContext())` l’appel est effectué à partir de votre activité principale.

   For more information, see Configuration methods.[](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)

* Ensure that the required permissions for the Mobile SDK are present in the  file:`AndroidManifest.xml`

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si le paramètre `referrerTimeout` est défini sur 5 dans le fichier ADMobileConfig.json, vous devez envoyer le mode d’installation dans un délai de 5 secondes après l’installation et le lancement de l’application pour la première fois afin que les informations du référent soient ajoutées à l’accès à l’installation.

   For manual testing, we recommend that you increase the  to 10-15 seconds, so that you have sufficient time to send the referrer information before the install hit is processed.`referrerTimeout`

* Run all the steps in Testing Marketing Link acquisition and ensure that you execute the  command first and then the following:[](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)`adb shell`

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>To process the referrer intent correctly, you must run these two commands independently. Otherwise  will double escape the referrer information and the data received by the broadcast receiver will be incomplete.`adb`


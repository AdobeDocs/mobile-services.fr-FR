---
description: Cette rubrique explique comment commencer à utiliser les composants Xamarin pour le SDK 4.x des solutions mobiles.
keywords: Xamarin
seo-description: Cette rubrique explique comment commencer à utiliser les composants Xamarin pour le SDK 4.x des solutions mobiles.
seo-title: Composants Xamarin pour SDK des solutions Experience Cloud 4.x
solution: Marketing Cloud,Developer
title: Composants Xamarin pour SDK des solutions Experience Cloud 4.x
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Cette rubrique explique comment commencer à utiliser les composants Xamarin pour le SDK 4.x des solutions mobiles.

Dernière mise à jour : **10 janvier 2019**

## Prise en main {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Le SDK mobile Adobe n’est plus disponible dans le magasin de composants Xamarin ou dans la galerie NuGet. Pour télécharger les composants Xamarin, accédez à [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importez le composant ADBMobile dans votre projet Xamarin.Android :

1. Open your Xamarin project

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/Android folder.`ADBMobile.XamarinAndroidBinding.dll`****

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Ajoutez des autorisations pour :

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. If you are using In-app messaging, add the following activity and receiver :

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. If you are using acquisition, add the following receiver :

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importez le composant ADBMobile dans votre projet Xamarin.iOS :

1. Ouvrez votre projet Xamarin.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/ios-unified folder.`ADBMobile.XamarinIOSBinding.dll`****

1. Ajoutez le fichier `ADBMobileConfig.json` au projet.



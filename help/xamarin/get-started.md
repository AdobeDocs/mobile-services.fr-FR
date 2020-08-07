---
description: Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK des solutions mobiles 4.x.
keywords: Xamarin
seo-description: Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK des solutions mobiles 4.x.
seo-title: Composants Xamarin pour le SDK des solutions Experience Cloud 4.x
solution: Marketing Cloud,Developer
title: Composants Xamarin pour le SDK des solutions Experience Cloud 4.x
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 3%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK des solutions mobiles 4.x.

Last Updated: **January 10, 2019**

## Prise en main {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>adobe Mobile SDK n’est plus disponible dans le magasin de composants Xamarin ni dans la galerie NuGet. Pour télécharger les composants Xamarin, accédez à [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importez le composant ADBMobile dans votre projet Xamarin.Android :

1. Ouvrez votre projet Xamarin
1. Ouvrez la boîte de dialogue **[!UICONTROL Références]** et cliquez sur l’onglet Assemblage **** .Net.
1. Sélectionnez `ADBMobile.XamarinAndroidBinding.dll` dans le dossier **[!UICONTROL lib/Android]** .
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. Ajoutez des autorisations pour :

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Si vous utilisez la messagerie in-app, ajoutez l’activité et le destinataire suivants :

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Si vous utilisez l’acquisition, ajoutez le destinataire suivant :

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
1. Ouvrez la boîte de dialogue **[!UICONTROL Références]** et cliquez sur l’onglet Assemblage **** .Net.
1. Sélectionnez `ADBMobile.XamarinIOSBinding.dll` dans le dossier unifié **** lib/ios.
1. ajoutez votre `ADBMobileConfig.json` fichier sur le projet.

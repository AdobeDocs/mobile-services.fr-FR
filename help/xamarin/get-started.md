---
description: Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK 4.x pour solutions mobiles.
keywords: Xamarin
seo-description: Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK 4.x pour solutions mobiles.
seo-title: Composants Xamarin pour le SDK 4.x pour solutions Experience Cloud
solution: Experience Cloud
title: Composants Xamarin pour le SDK 4.x pour solutions Experience Cloud
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '199'
ht-degree: 100%

---


# Composants Xamarin pour le SDK 4.x des solutions Experience Cloud {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Cette rubrique décrit comment commencer à utiliser les composants Xamarin pour le SDK 4.x pour solutions mobiles.

Dernière mise à jour : **10 janvier 2019**

## Prise en main {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Le SDK Mobile Adobe n’est plus disponible dans la boutique de composants Xamarin ni dans la galerie NuGet. Pour télécharger les composants Xamarin, accédez à [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importez le composant ADBMobile dans votre projet Xamarin.Android :

1. Ouvrez votre projet Xamarin
1. Ouvrez la boîte de dialogue **[!UICONTROL Références]** et cliquez sur l’onglet **[!UICONTROL Assembly .Net]**.
1. Sélectionnez `ADBMobile.XamarinAndroidBinding.dll` dans le dossier **[!UICONTROL lib/Android]**.
1. Ajoutez le fichier `ADBMobileConfig.json` au dossier **[!UICONTROL Ressources]** du projet.
1. Ajoutez des autorisations pour :

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Si vous utilisez la messagerie in-app, ajoutez l’activité et le destinataire suivants :

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Si vous utilisez l’acquisition, ajoutez le destinataire suivant :

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importez le composant ADBMobile dans votre projet Xamarin.iOS :

1. Ouvrez votre projet Xamarin.
1. Ouvrez la boîte de dialogue **[!UICONTROL Références]** et cliquez sur l’onglet **[!UICONTROL Assembly .Net]**.
1. Sélectionnez `ADBMobile.XamarinIOSBinding.dll` dans le dossier **[!UICONTROL lib/ios-unified]**.
1. Ajoutez votre fichier `ADBMobileConfig.json` au projet.

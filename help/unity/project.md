---
description: valeur nulle
keywords: Unity
seo-description: valeur nulle
seo-title: Building your project
solution: Marketing Cloud,Developer
title: Building your project
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

Lorsque vous créez une application pour iOS, un projet Xcode est créé. Par défaut, les fichiers `ADBMobileWrapper.mm` et `AdobeMobileLibrary.a` se trouvent dans le groupe Bibliothèques du nouveau projet. Suivez les étapes manuelles suivantes pour créer l’application :

1. Ajoutez le fichier `ADBMobileConfig.json` au projet.

   Assurez-vous que toutes les cibles nécessaires font partie de la compilation.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(This library might be linked already.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Lorsque vous créez une application pour Android, le fichier `apk` comprend déjà le fichier `ADBMobileConfig.json` à l’emplacement correct. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

Pour utiliser votre propre fichier manifest personnalisé, les changements suivants doivent être apportés.

Ajoutez des autorisations pour :

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

If you are using In-app messaging, add the following activity and receiver:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

If you are using acquisition, add the following receiver:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```

---
description: Création de projets iOS
keywords: Unity
solution: Experience Cloud Services
title: Création de votre projet
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Création de votre projet{#building-your-project}

## iOS

Lorsque vous créez pour iOS, un projet Xcode est créé. Par défaut, la variable `ADBMobileWrapper.mm` et  `AdobeMobileLibrary.a` Les fichiers se trouvent dans le groupe Bibliothèques de votre nouveau projet. Effectuez les étapes manuelles suivantes pour créer votre application :

1. Ajoutez votre fichier `ADBMobileConfig.json` au projet.

   Assurez-vous qu’il est membre de la génération des cibles nécessaires.

1. Dans le **[!UICONTROL Phases de création]** de votre projet, ajoutez un lien vers les bibliothèques suivantes :

   * `SystemConfiguration.framework`
(Cette bibliothèque peut déjà être liée.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Pour utiliser les messages In-App de notification locale du SDK, vous devez appeler `ADBMobile.EnableLocalNotifications();` à partir de la méthode Start dans votre première scène Unity.

## Android

Lorsque vous créez pour Android, la variable `apk` inclut déjà le fichier `ADBMobileConfig.json` au bon emplacement. Par défaut, la variable `AndroidManifest.xml` dans votre `/Plugins/Android` est également utilisé.

Si vous devez utiliser votre propre fichier de manifeste personnalisé, les modifications suivantes doivent être ajoutées.

Ajoutez des autorisations pour :

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Si vous utilisez la messagerie in-app, ajoutez l’activité et le destinataire suivants :

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

---
description: Création de projets iOS
keywords: Unity
solution: Experience Cloud
title: Création de votre projet
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Création de votre projet{#building-your-project}

## iOS

Lorsque vous créez pour iOS, un projet Xcode est créé. Par défaut, les fichiers `ADBMobileWrapper.mm` et `AdobeMobileLibrary.a` se trouvent dans le groupe Bibliothèques de votre nouveau projet. Suivez les étapes manuelles suivantes pour créer votre application :

1. Ajoutez votre fichier `ADBMobileConfig.json` au projet.

   Assurez-vous qu’il est membre de la build toutes les cibles nécessaires.

1. Dans l&#39;onglet **[!UICONTROL Build Phases]** de votre projet, ajoutez un lien vers les bibliothèques suivantes :

   * `SystemConfiguration.framework`
(Cette bibliothèque peut déjà être liée.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Pour utiliser les messages in-app de notification locale du SDK, vous devez appeler `ADBMobile.EnableLocalNotifications();` à partir de la méthode de Début dans votre première scène Unity.

## Android

Lorsque vous créez pour Android, le fichier `apk` inclut déjà le fichier `ADBMobileConfig.json` à l’emplacement approprié. Par défaut, le fichier `AndroidManifest.xml` de votre dossier `/Plugins/Android` est également utilisé.

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

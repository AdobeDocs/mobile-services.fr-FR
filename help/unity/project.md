---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Création de votre projet
solution: Experience Cloud
title: Création de votre projet
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# Création de votre projet{#building-your-project}

## iOS

Lorsque vous créez pour iOS, un projet Xcode est créé. Par défaut, les fichiers `ADBMobileWrapper.mm` et `AdobeMobileLibrary.a` se trouvent dans le groupe Bibliothèques de votre nouveau projet. Suivez les étapes manuelles suivantes pour créer votre application :

1. Ajoutez votre fichier `ADBMobileConfig.json` au projet.

   Assurez-vous qu’il est membre de la build toutes les cibles nécessaires.

1. Dans l’onglet **[!UICONTROL Build Phases]** (Créer les phases) de votre projet, ajoutez un lien vers les bibliothèques suivantes :

   * `SystemConfiguration.framework`
(Cette bibliothèque peut déjà être liée.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Pour utiliser les messages in-app de notification locale du SDK, vous devez appeler `ADBMobile.EnableLocalNotifications();` à partir de la méthode de Début dans votre première scène Unity.

## Android

Lorsque vous créez pour Android, le `apk` fichier inclut déjà le `ADBMobileConfig.json` fichier à l’emplacement approprié. Par défaut, le `AndroidManifest.xml` fichier de votre `/Plugins/Android` dossier est également utilisé.

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

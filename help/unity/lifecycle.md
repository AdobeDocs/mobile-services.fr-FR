---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Mise en œuvre du cycle de vie
solution: Experience Cloud
title: Mise en œuvre du cycle de vie
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# Mise en œuvre du cycle de vie{#implement-lifecycle}

Pour plus d’informations sur les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie mis en oeuvre, voir Mesures de [cycle de vie dans Android](/help/android/metrics.md) ou [cycle de vie dans iOS](/help/ios/metrics.md).

## iOS

Les mesures de cycle de vie sont automatiquement collectées dans iOS.

## Android

Dans votre script Unity, vous définissez le contexte de l’application pour le SDK Android. ajoutez le code suivant à la `Awake()` fonction de votre PREMIÈRE scène :

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Pour collecter des mesures de cycle de vie, ajoutez le code suivant à tous vos scripts de scène :

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```


---
description: Mesures et dimensions pouvant être mesurées automatiquement par la bibliothèque mobile
keywords: Unity
solution: Experience Cloud Services
title: Mise en œuvre du cycle de vie
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Mise en œuvre du cycle de vie{#implement-lifecycle}

Pour plus d’informations sur les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie mis en oeuvre, voir [Mesures de cycle de vie sous Android](/help/android/metrics.md) ou [Cycle de vie dans iOS](/help/ios/metrics.md).

## iOS

Les mesures de cycle de vie sont automatiquement collectées dans iOS.

## Android

Dans le script Unity, définissez le contexte de l’application pour le SDK Android. Ajoutez le code suivant au `Awake()` fonction de votre PREMIÈRE scène :

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

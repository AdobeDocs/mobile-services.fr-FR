---
description: valeur nulle
keywords: Unity
seo-description: valeur nulle
seo-title: Mise en œuvre du cycle de vie
solution: Marketing Cloud,Développeur
title: Mise en œuvre du cycle de vie
uuid: 7ff2c194-569c-42a6-922d-dcccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Mise en œuvre du cycle de vie{#implement-lifecycle}

Pour plus d’informations sur les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie mis en oeuvre, voir Mesures de [cycle de vie dans Android](/help/android/metrics.md) ou [Cycle de vie dans iOS](/help/ios/metrics.md).

## iOS

Les mesures de cycle de vie sont automatiquement collectées dans iOS.

## Android

Dans le script Unity, définissez le contexte de l’application pour le SDK Android. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Pour collecter des mesures de cycle de vie, ajoutez le code suivant à tous les scripts de la scène :

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


---
description: valeur nulle
keywords: Unity
seo-description: valeur nulle
seo-title: Mise en œuvre du cycle de vie
solution: Marketing Cloud, développeur
title: Mise en œuvre du cycle de vie
uuid: 7 ff 2 c 194-569 c -42 a 6-922 d-dccd 2 aa 9 eb 8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Mise en œuvre du cycle de vie{#implement-lifecycle}

Pour plus d'informations sur les mesures et dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie implémenté, voir [Mesures de cycle de vie dans Android](/help/android/metrics.md) ou [Lifecycle dans ios](/help/ios/metrics.md).

## iOS

Les mesures de cycle de vie sont automatiquement collectées dans ios.

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


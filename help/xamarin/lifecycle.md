---
description: Informations destinées à vous aider à mettre en oeuvre des mesures de cycle de vie pour Android. Les mesures de cycle de vie sont automatiquement collectées pour iOS.
keywords: Xamarin
seo-description: Informations destinées à vous aider à mettre en oeuvre des mesures de cycle de vie pour Android. Les mesures de cycle de vie sont automatiquement collectées pour iOS.
seo-title: Mise en œuvre du cycle de vie
solution: Experience Cloud
title: Mise en œuvre du cycle de vie
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# Mise en œuvre du cycle de vie {#implement-lifecycle}

Ces informations vous aident à mettre en oeuvre des mesures de cycle de vie pour Android.

>[!TIP]
>
>Les mesures de cycle de vie sont automatiquement collectées pour iOS.

Pour les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie mis en oeuvre, voir Mesures [du](/help/ios/metrics.md)cycle de vie.

## iOS

Sous iOS, les mesures de cycle de vie sont automatiquement collectées.

## Android

Dans votre activité principale, définissez le contexte de l’application pour le SDK Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

Dans chaque activité, implémentez des appels de cycle de vie.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```

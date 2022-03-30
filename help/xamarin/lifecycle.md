---
description: Informations relatives à la mise en oeuvre des mesures de cycle de vie pour Android. Les mesures de cycle de vie sont automatiquement collectées pour iOS.
keywords: Xamarin
solution: Experience Cloud Services
title: Mise en œuvre du cycle de vie
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# Mise en œuvre du cycle de vie {#implement-lifecycle}

Ces informations vous aident à mettre en oeuvre des mesures de cycle de vie pour Android.

>[!TIP]
>
>Les mesures de cycle de vie sont automatiquement collectées pour iOS.

Pour connaître les mesures et les dimensions qui peuvent être mesurées automatiquement par la bibliothèque mobile une fois le cycle de vie mis en oeuvre, voir [Mesures de cycle de vie](/help/ios/metrics.md).

## iOS

Dans iOS, les mesures de cycle de vie sont automatiquement collectées.

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

Mettez en oeuvre les appels de cycle de vie dans chaque activité.

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

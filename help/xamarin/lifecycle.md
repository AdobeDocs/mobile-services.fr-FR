---
description: Informations relatives à la mise en œuvre des mesures de cycle de vie pour Android. Sous iOS, les mesures de cycle de vie sont automatiquement collectées.
keywords: Xamarin
seo-description: Informations relatives à la mise en œuvre des mesures de cycle de vie pour Android. Sous iOS, les mesures de cycle de vie sont automatiquement collectées.
seo-title: Mettre en oeuvre le cycle de vie
solution: Marketing Cloud,Developer
title: Mettre en oeuvre le cycle de vie
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Ces informations vous aident à mettre en oeuvre des mesures de cycle de vie pour Android.

>[!TIP]
>
>Sous iOS, les mesures de cycle de vie sont automatiquement collectées.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

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

In every activity, implement lifecycle calls.

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

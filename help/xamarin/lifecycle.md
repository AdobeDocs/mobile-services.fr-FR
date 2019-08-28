---
description: Informations relatives à la mise en œuvre des mesures de cycle de vie pour Android. Sous iOS, les mesures de cycle de vie sont automatiquement collectées.
keywords: Xamarin
seo-description: Informations relatives à la mise en œuvre des mesures de cycle de vie pour Android. Sous iOS, les mesures de cycle de vie sont automatiquement collectées.
seo-title: Mise en œuvre du cycle de vie
solution: Marketing Cloud, développeur
title: Mise en œuvre du cycle de vie
uuid: 6 dccc 12 e -8 b 57-4231-9 c 74-d 47 bc 0 ac 93 ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Ces informations vous aident à mettre en œuvre des mesures de cycle de vie pour Android.

>[!TIP]
>
>Sous iOS, les mesures de cycle de vie sont automatiquement collectées.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

Dans ios, les mesures de cycle de vie sont automatiquement collectées.

## Android

Dans votre activité principale, définissez le contexte de l'application pour le SDK Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

Dans chaque activité, implémentez les appels du cycle de vie.

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

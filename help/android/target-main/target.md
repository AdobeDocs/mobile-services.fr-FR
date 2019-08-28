---
description: Vous pouvez fournir un contenu ciblé dans les applications Android.
keywords: android ; library ; mobile ; sdk
seo-description: Vous pouvez fournir un contenu ciblé dans les applications Android.
seo-title: Configuration de Target
solution: Marketing Cloud, Analytics
title: Configuration de Target
topic: Développeur et mise en œuvre
uuid: 09 fe 2 c 9 c -7 b 60-49 c 3-bb 9 d -36 a 30 ce 7 c 350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Vous pouvez fournir un contenu ciblé dans les applications Android.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Obligatoire)** La `setContext()` méthode doit être appelée une fois dans `onCreate()` la méthode de votre activité principale.

Par exemple :

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si vous avez déjà ajouté cet appel de méthode lorsque vous avez mis en œuvre Analytics ou gestion de l’audience, il n’est pas nécessaire de le faire à nouveau.

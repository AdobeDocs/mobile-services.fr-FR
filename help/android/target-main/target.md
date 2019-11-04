---
description: Vous pouvez fournir un contenu ciblé dans les applications Android.
keywords: android;library;mobile;sdk
seo-description: Vous pouvez fournir un contenu ciblé dans les applications Android.
seo-title: Configuration de Target
solution: Experience Cloud,Analytics
title: Configuration de Target
topic: Développeur et mise en œuvre
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Configuration de Target {#target-configuration}

Vous pouvez fournir un contenu ciblé dans les applications Android.

## Définition du contexte de l’application {#section_37CAE496FF894FCA821F7760605574CA}

**(Obligatoire)** La méthode `setContext()` doit être appelée une fois dans la méthode `onCreate()` de l’activité principale.

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

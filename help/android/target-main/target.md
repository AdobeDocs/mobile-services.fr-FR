---
description: Vous pouvez fournir un contenu ciblé dans les applications Android.
keywords: android;library;mobile;sdk
seo-description: Vous pouvez fournir un contenu ciblé dans les applications Android.
seo-title: Configuration de Target
solution: Experience Cloud,Analytics
title: Configuration de Target
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '72'
ht-degree: 100%

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

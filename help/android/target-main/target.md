---
description: Vous pouvez fournir un contenu ciblé dans les applications Android.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Configuration de Target
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '66'
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

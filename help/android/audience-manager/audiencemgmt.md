---
description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
keywords: android;library;mobile;sdk
seo-description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
seo-title: Configuration d’Audience Manager
solution: Experience Cloud,Analytics
title: Configuration d’Audience Manager
topic: Développeur et mise en œuvre
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Configuration d’Audience Manager{#audience-manager-configuration}

Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès d’Audience Manager.

## Définition du contexte de l’application {#section_37CAE496FF894FCA821F7760605574CA}

**(Obligatoire)** La méthode `setContext()` doit être appelée une fois dans la méthode `onCreate()` de l’activité principale.

Voici l’exemple de code pour cette méthode :

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si vous avez ajouté cet appel de méthode lors de la mise en œuvre d’Analytics ou de Target, il n’est pas nécessaire de le faire à nouveau.

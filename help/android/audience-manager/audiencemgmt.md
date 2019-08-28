---
description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
keywords: android ; library ; mobile ; sdk
seo-description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
seo-title: Configuration d'Audience Manager
solution: Marketing Cloud, Analytics
title: Configuration d'Audience Manager
topic: Développeur et mise en œuvre
uuid: f 68 d 5 b 2 e-fa 2 c -4 db 6-98 ad-d 1855 a 2 c 45 ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Vous pouvez envoyer des signaux et récupérer des segments de visiteurs depuis Audience Manager.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Obligatoire)** La `setContext()` méthode doit être appelée une fois dans `onCreate()` la méthode de votre activité principale.

Voici l’exemple de code pour cette méthode :

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si vous avez ajouté cet appel de méthode lorsque vous avez implémenté Analytics ou Target, il n'est pas nécessaire de l'ajouter à nouveau.

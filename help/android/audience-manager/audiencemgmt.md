---
description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
keywords: android;library;mobile;sdk
seo-description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
seo-title: Configuration d’Audience Manager
solution: Marketing Cloud,Analytics
title: Configuration d’Audience Manager
topic: Développeur et mise en œuvre
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Vous pouvez envoyer des signaux et récupérer des segments de visiteurs à partir d’Audience Manager.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Obligatoire)** La `setContext()` méthode doit être appelée une seule fois dans la `onCreate()` méthode de votre activité principale.

Voici l’exemple de code pour cette méthode :

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

If you added this method call when you implemented Analytics or Target, you do not need to add it again.

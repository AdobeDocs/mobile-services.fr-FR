---
description: Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès de la gestion de l’audience.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Configuration d’Audience Manager
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 100%

---

# Configuration d’Audience Manager{#audience-manager-configuration}

Vous pouvez envoyer des signaux et récupérer des segments de visiteurs auprès d’Audience Manager.

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

---
description: La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur Android. La valeur peut être utilisée pour stocker des valeurs de durée de vie (achats, vues des publicités, affichages complets de vidéos, partages sur les médias sociaux, chargement de photos, etc.).
seo-description: La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur Android. La valeur peut être utilisée pour stocker des valeurs de durée de vie (achats, vues des publicités, affichages complets de vidéos, partages sur les médias sociaux, chargement de photos, etc.).
seo-title: Valeur de durée de vie visiteur
solution: Experience Cloud,Analytics
title: Valeur de durée de vie visiteur
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---


# Valeur de durée de vie visiteur {#visitor-lifetime-value}

La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur Android. La valeur peut être utilisée pour stocker des valeurs de durée de vie (achats, vues des publicités, affichages complets de vidéos, partages sur les médias sociaux, chargement de photos, etc.).

À chaque fois que vous envoyez une valeur avec `trackLifetimeValueIncrease`, la valeur est ajoutée à la valeur existante. La valeur de durée de vie est stockée sur l’appareil et peut être récupérée à tout moment en appelant `lifetimeValue`.

## Suivi de la valeur de durée de vie des visiteurs {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration au projet IntelliJ IDEA ou Eclipse* dans [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Appelez `trackLifetimeValueIncrease` avec le montant permettant d’augmenter la valeur :

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Envoi de données supplémentaires {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre la valeur de durée de vie, vous pouvez également envoyer des données contextuelles supplémentaires avec chaque appel d’action de suivi :

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

Les valeurs de données contextuelles doivent être mappées à des variables personnalisées dans Adobe Mobile Services :

![](assets/map-variable-context-ltv.png)


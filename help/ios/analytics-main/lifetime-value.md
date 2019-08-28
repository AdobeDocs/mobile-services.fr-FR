---
description: La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur.
seo-description: La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur.
seo-title: Valeur de durée de vie du visiteur
solution: Marketing Cloud, Analytics
title: Valeur de durée de vie du visiteur
topic: Développeur et mise en œuvre
uuid: d 830 d 18 b -4313-43 bb -8 d 75-3789869 d 0 f 1 d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

La valeur de durée de vie vous permet de mesurer et de cibler une valeur de durée de vie pour chaque utilisateur.

À chaque fois que vous envoyez une valeur avec `trackLifetimeValueIncrease`, la valeur est ajoutée à la valeur existante. La valeur de durée de vie est stockée sur l’appareil et peut être récupérée à tout moment en appelant `lifetimeValue`. Cette procédure peut être utilisée pour stocker des valeurs de durée de vie (achats, vues des publicités, affichages complets de vidéos, partages sur les médias sociaux, chargement de photos, etc.).

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Appelez `trackLifetimeValueIncrease` avec le montant permettant d’augmenter la valeur :

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre la valeur de durée de vie, vous pouvez joindre des données contextuelles supplémentaires à chaque appel d’action de suivi :

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Les valeurs de données contextuelles doivent être mises en correspondance avec les variables personnalisées :

![](assets/map-variable-context-ltv.png)


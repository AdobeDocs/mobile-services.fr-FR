---
description: La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK iOS 4.x, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products directement sur l’appel de serveur.
seo-description: La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK iOS 4.x, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products directement sur l’appel de serveur.
seo-title: Variable products
solution: Marketing Cloud, Analytics
title: Variable products
topic: Développeur et mise en œuvre
uuid: 6 ece 4 d 27-ef 86-435 c-a 6 f 7-bd 76 be 1 c 95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK iOS 4.x, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products directement sur l’appel de serveur.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

Par exemple :

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* est définie directement sur la demande d'image et que les autres variables sont définies comme données contextuelles. Toutes les variables de données contextuelles doivent être mises en correspondance à l’aide des règles de traitement :

![](assets/map-products.png)

Il n’est pas nécessaire de mettre en correspondance la variable *`products`* à l’aide des règles de traitement, car elle est définie directement sur la demande d’image par le SDK.

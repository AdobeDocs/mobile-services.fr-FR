---
description: Impossible de définir la variable products à l'aide de règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits directement sur l’appel au serveur.
seo-description: Impossible de définir la variable products à l'aide de règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits directement sur l’appel au serveur.
seo-title: Variable products
solution: Experience Cloud,Analytics
title: Variable products
topic: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 13%

---


# Variable products {#products-variable}

Impossible de définir la variable products à l&#39;aide de règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits directement sur l’appel au serveur.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Par exemple :

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* est définie directement sur la demande d’image, tandis que les autres variables sont définies en tant que données contextuelles. Toutes les variables de données contextuelles doivent être mises en correspondance à l’aide de règles de traitement :

![](assets/products-procrules.png)

Il n’est pas nécessaire de mapper la *`products`* variable à l’aide de règles de traitement, car elle est directement définie sur la demande d’image par le SDK.

---
description: La variable products ne peut pas être définie à l’aide de règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits directement sur l’appel au serveur.
solution: Experience Cloud Services,Analytics
title: Variable products
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Variable products{#products-variable}

La variable products ne peut pas être définie à l’aide de règles de traitement. Dans le SDK mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits directement sur l’appel au serveur.

Pour définir la variable *`products`* , définissez une clé de données contextuelles sur `"&&products"`et définissez la valeur à l’aide de la syntaxe définie pour la variable *`products`*:

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

*`products`* est définie directement sur la demande d’image, tandis que les autres variables sont définies en tant que données contextuelles. Toutes les variables de données contextuelles doivent être mappées à l’aide de règles de traitement :

![](assets/products-procrules.png)

Vous n’avez pas besoin de mapper la variable *`products`* à l’aide des règles de traitement, car elle est définie directement sur la demande d’image par le SDK.

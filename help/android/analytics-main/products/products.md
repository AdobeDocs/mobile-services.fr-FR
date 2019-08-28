---
description: La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products sur l’appel de serveur.
keywords: android ; library ; mobile ; sdk
seo-description: La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products sur l’appel de serveur.
seo-title: Variable products
solution: Marketing Cloud, Analytics
title: Variable products
topic: Développeur et mise en œuvre
uuid: f 4484022-cb 8 b -4 dea -9209-5 a 110 ba 607 df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

La variable products ne peut pas être définie à l’aide des règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir la variable products sur l’appel de serveur.

To set the *products* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *products* variable:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

Par exemple :

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

The *products* variable is set on the image request, and the other variables are set as context data. Toutes les variables de données contextuelles doivent être mises en correspondance à l’aide des règles de traitement :

![](assets/map-products.png)

Il n’est pas nécessaire de mettre en correspondance la variable *variable products* à l'aide de règles de traitement, car cette variable est directement définie sur la demande d'image par le SDK.

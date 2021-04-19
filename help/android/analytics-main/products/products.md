---
description: La variable products ne peut pas être définie à l’aide de règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits sur l’appel au serveur.
keywords: android;library;mobile;sdk
seo-description: La variable products ne peut pas être définie à l’aide de règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits sur l’appel au serveur.
seo-title: Variable products
solution: Experience Cloud,Analytics
title: Variable products
topic-fix: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
exl-id: 1d850ce1-6fd4-463e-8949-8b8cf40d8467
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---

# Variable products {#products-variable}

La variable products ne peut pas être définie à l’aide de règles de traitement. Dans le SDK Mobile, vous devez utiliser une syntaxe spéciale dans le paramètre de données contextuelles pour définir les produits sur l’appel au serveur.

Pour définir la variable *products*, définissez une clé de données contextuelles sur `"&&products"`, puis définissez la valeur en utilisant la syntaxe définie pour la variable *products* :

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

La variable *products* est définie sur la demande d’image ; les autres variables sont définies comme données contextuelles. Toutes les variables de données contextuelles doivent être mises en correspondance à l’aide des règles de traitement :

![](assets/map-products.png)

Il n’est pas nécessaire de mettre en correspondance la variable  *products* en utilisant les règles de traitement, car cette variable est définie directement sur la demande d’image par le SDK.

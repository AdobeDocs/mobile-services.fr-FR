---
description: Voici un exemple de variable products avec des eVars de marchandisage et des événements spécifiques à un produit.
keywords: android ; library ; mobile ; sdk
seo-description: Voici un exemple de variable products avec des eVars de marchandisage et des événements spécifiques à un produit.
seo-title: Variable products avec des eVars de marchandisage et des événements spécifiques à un produit
solution: Marketing Cloud, Analytics
title: Variable products avec des eVars de marchandisage et des événements spécifiques à un produit
topic: Développeur et mise en œuvre
uuid: 64 f 822 a 0-6 ccf -48 e 7-8886-31 b 93 d 8198 a 3
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

Voici un exemple de variable products avec des eVars de marchandisage et des événements spécifiques à un produit.

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Si vous déclenchez un événement spécifique au produit à l'aide de *`&&products`* la variable, vous devez également définir cet événement dans *`&&events`* la variable. Si vous ne définissez pas cet événement, il est filtré au cours du traitement.


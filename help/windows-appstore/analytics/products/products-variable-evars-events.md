---
description: Voici un exemple de variable products avec eVars de marchandisage et événements spécifiques aux produits.
seo-description: Voici un exemple de variable products avec eVars de marchandisage et événements spécifiques aux produits.
seo-title: Variable products avec des eVars de marchandisage et des événements spécifiques à un produit
solution: Marketing Cloud, Analytics
title: Variable products avec des eVars de marchandisage et des événements spécifiques à un produit
topic: Développeur et mise en œuvre
uuid: 94 e 882 e 4-b 19 d -4 c 48-9 dfb -331465490347
translation-type: tm+mt
source-git-commit: b630c5cf09be7fbe31018cbf50564001eb6e2a5a

---


# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

Voici un exemple de variable products avec eVars de marchandisage et événements spécifiques aux produits.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Si vous déclenchez un événement spécifique au produit à l'aide de *`&&products`* la variable, vous devez également définir cet événement dans *`&&events`* la variable ; sinon, l'événement est filtré au cours du traitement.


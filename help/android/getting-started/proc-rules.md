---
description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-title: Règles de traitement et données contextuelles.
solution: Marketing Cloud,Analytics
title: Règles de traitement et données contextuelles.
topic: Développeur et mise en œuvre
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Lors de l’utilisation des règles de traitement, gardez à l’esprit les informations suivantes :

* Regroupez les variables de données contextuelles à l’aide d’espaces de noms, car cela permet de conserver un ordre logique. Par exemple, pour recueillir des informations sur un produit, vous pouvez définir les variables suivantes :

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement, ce qui permet de voir rapidement les variables qui sont dans le même espace de noms.

   Évitez de nommer les clés de données contextuelles en utilisant le numéro evar ou prop :

   ```js
   "eVar1":"jimbo"
   ```

   La dénomination selon le numéro evar ou prop peut *légèrement* faciliter la correspondance unique dans les règles de traitement, mais cela nuit à la lisibilité lors du débogage et des mises à jour futures du code, qui peuvent ainsi devenir plus difficiles. Nous vous recommandons vivement d’utiliser plutôt des noms explicites pour les clés et les valeurs :

   ```js
   "username":"jimbo"
   ```

* Les variables de contexte qui définissent les événements de compteur doivent être définies sur 1 :

   ```js
   "logon":"1"
   ```

* Les variables de données contextuelles qui définissent les événements d’incrémentation peuvent avoir l’événement comme clé et le montant à incrémenter comme valeur :

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe réserve l’espace de noms `"a."`. En outre, pour éviter des collisions, les variables de données contextuelles doivent être uniques dans votre société de connexion.


---
description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-title: Règles de traitement et données contextuelles.
solution: Experience Cloud,Analytics
title: Règles de traitement et données contextuelles.
topic: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 44%

---


# Règles de traitement et données contextuelles{#processing-rules-and-context-data}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports. Pour plus d’informations, reportez-vous à la section [Règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Lorsque vous utilisez des règles de traitement, tenez compte des informations suivantes :

* Regroupez vos variables de données contextuelles à l’aide d’espaces de nommage, car cela vous permet de conserver un ordre logique. Par exemple, pour collecter des informations sur un produit, vous pouvez définir les variables suivantes :

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement, ce qui vous permet de voir rapidement quelles variables se trouvent dans le même espace de nommage.

   Evitez d’attribuer un nom aux clés de données contextuelles en utilisant la variable evar ou le numéro prop :

   ```js
   "eVar1":"jimbo"
   ```

   Cela peut faciliter *légèrement* la tâche lorsque vous effectuez le mappage ponctuel dans les règles de traitement, mais vous perdez la lisibilité lors du débogage et des futures mises à jour du code, ce qui peut s’avérer plus difficile. Nous vous recommandons plutôt d’utiliser des noms descriptifs pour les clés et les valeurs :

   ```js
   "username":"jimbo"
   ```

* Les variables contextuelles qui définissent les événements de compteur doivent être définies sur 1 :

   ```js
   "logon":"1"
   ```

* Les variables de données contextuelles qui définissent les événements incrémenteurs peuvent avoir le événement comme clé et le montant à incrémenter comme valeur :

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe réserve l’espace de noms « `"a."` ». En outre, pour éviter des collisions, les variables de données contextuelles doivent être uniques dans votre société de connexion.


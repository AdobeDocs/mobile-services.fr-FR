---
description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-title: Règles de traitement et données contextuelles.
solution: Experience Cloud,Analytics
title: Règles de traitement et données contextuelles.
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---


# Règles de traitement et données contextuelles {#processing-rules-and-context-data}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.

Pour plus d’informations, voir la vidéo et les rubriques suivants :

* [Formation aux règles de traitement](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* Obtention de l’autorisation d’utiliser des règles de traitement

   Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Lorsque vous utilisez des règles de traitement, tenez compte des informations suivantes :

* Regroupez vos variables de données contextuelles à l’aide d’espaces de noms, car cela vous permet de conserver un ordre logique.

   Par exemple, si vous souhaitez collecter des informations sur un produit, vous pouvez définir les variables suivantes :

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement, ce qui vous permet de voir rapidement quelles variables se trouvent dans le même espace de noms.

   Évitez d’attribuer un nom aux clés de données contextuelles en utilisant la variable evar ou le numéro prop :

   ```js
   "eVar1":"jimbo"
   ```

   Cela pourrait faciliter *légèrement* le mapping ponctuel dans les règles de traitement, mais vous perdriez la lisibilité pendant le débogage et lors des futures mises à jour du code, ce qui pourrait s’avérer plus difficile. Utilisez plutôt des noms explicites pour les clés et les valeurs :

   ```js
   "username":"jimbo"
   ```

* Les variables contextuelles qui définissent les événements de compteur doivent être définies sur 1 :

   ```js
   "logon":"1"
   ```

* Les variables de données contextuelles qui définissent les événements incrémenteurs peuvent avoir l’événement comme clé et la quantité à incrémenter comme valeur :

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe réserve l’espace de noms « `a.` ». À part cette restriction, pour éviter les collisions, la seule exigence est que les variables de données contextuelles soient uniques dans votre société de connexion.


---
description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans des variables de données contextuelles vers des eVars, des props et d’autres variables pour la création de rapports.
solution: Experience Cloud,Analytics
title: Règles de traitement et données contextuelles.
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 70%

---

# Règles de traitement et données contextuelles {#processing-rules-and-context-data}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans des variables de données contextuelles vers des eVars, des props et d’autres variables pour la création de rapports.

Pour plus d’informations, voir la vidéo et les rubriques suivants :

* [Formation aux règles de traitement](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* Obtention de l’autorisation d’utiliser des règles de traitement

   Pour plus d’informations sur les règles de traitement, voir [Présentation des règles de traitement](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) dans la documentation Adobe Analytics.

Lorsque vous utilisez des règles de traitement, tenez compte des informations suivantes :

* Regroupez vos variables de données contextuelles à l’aide d’espaces de noms, car cela vous permet de conserver un ordre logique.

   Par exemple, si vous souhaitez collecter des informations sur un produit, vous pouvez définir les variables suivantes :

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement, ce qui vous permet de voir rapidement quelles variables se trouvent dans le même espace de noms.

   Évitez de nommer les clés de données contextuelles à l’aide de l’eVar ou du numéro de prop :

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

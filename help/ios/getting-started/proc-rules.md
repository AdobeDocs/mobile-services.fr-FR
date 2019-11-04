---
description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-description: Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.
seo-title: Règles de traitement et données contextuelles.
solution: Experience Cloud,Analytics
title: Règles de traitement et données contextuelles.
topic: Développeur et mise en œuvre
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Règles de traitement et données contextuelles{#processing-rules-and-context-data}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans les variables de données contextuelles vers des evars, props et autres variables pour la création de rapports.

Pour plus d’informations, voir la vidéo et les rubriques suivants :

* [Processing Rules Training](https://tv.adobe.com/embed/1181/16506/) (Formation aux règles de traitement) – Summit 2013
* Obtention de l’autorisation d’utiliser des règles de traitement

   Pour plus d’informations sur les règles de traitement, voir l’[Aperçu des règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Lors de l’utilisation des règles de traitement, prenez note des informations suivantes :

* Regroupez les variables de données contextuelles à l’aide d’espaces de noms, car cela permet de conserver un ordre logique.

   Si, par exemple, vous souhaitez collecter des informations sur un produit, vous pourriez définir les variables suivantes :

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

   Ceci pourrait *quelque peu* vous faciliter la tâche lorsque vous exécutez le mappage unique dans les règles de traitement, mais la lisibilité sera réduite au cours du débogage et des futures mises à jour de code, qui pourront alors s’avérer plus complexes. Utilisez plusieurs des noms explicites pour les clés et les valeurs :

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
>Adobe réserve l’espace de noms « `a.` ». À part cette restriction, pour éviter les collisions, la seule exigence est que les variables de données contextuelles soient uniques dans votre société de connexion.


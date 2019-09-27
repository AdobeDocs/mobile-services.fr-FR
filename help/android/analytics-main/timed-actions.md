---
description: Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-description: Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.
seo-title: Actions minutées
solution: Marketing Cloud,Analytics
title: Actions minutées
topic: Développeur et mise en œuvre
uuid: 5a48a580-b942-4e49-9f1b-078fea7fcdb
translation-type: tm+mt
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

---


# Timed actions {#timed-actions}

Les actions minutées permettent de mesurer la durée in-app et la durée totale entre le début et la fin d’une action. Le SDK calcule la durée dans chaque session et la durée totale entre toutes les sessions nécessaires pour terminer l’action. Vous pouvez utiliser les actions minutées pour définir des segments et comparer la durée d’achat, le niveau de transmission, le flux de passage en caisse, etc.

Les mesures suivantes sont signalées pour les actions minutées :

* Nombre total de secondes dans l’application entre le début et la fin (intersessions)
* Nombre total de secondes entre le début et la fin (heure de l’horloge)

Un rappel facultatif permet d’entreprendre des actions supplémentaires lorsque les actions minutées se terminent :

* Exécuter du code et ajouter une logique : logique personnalisée facultative reposant sur les résultats de la durée.
* Ajouter des données contextuelles avant de transmettre des durées.
* Annuler un accès et des durées non encore envoyés.

## Track timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* IntelliJ IDEA ou Eclipse dans l’implémentation et le cycle de vie [principaux](/help/android/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Appelez `trackTimedActionStart` et fournissez un nom d’action minutée et des données contextuelles facultatives.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Facultatif) À tout moment, vous pouvez appeler `trackTimedActionUpdate` avec le nom de l’action minutée pour ajouter des données contextuelles supplémentaires.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Une fois l’événement terminé, appelez `trackTimedActionEnd` et transmettez le nom de l’action minutée, puis `TimedActionBlock` (rappel), qui recherche toutes les données et calcule les durées.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Les mesures des événements minutés sont enregistrées dans des variables des solutions mobiles pour une création de rapports automatique.

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre le nom de l’action minutée, vous pouvez envoyer des données contextuelles supplémentaires avec les appels de début et de mise à jour d’action :

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

Les valeurs de données contextuelles doivent être mappées à des variables personnalisées dans Adobe Mobile Services :

![](assets/map-variable-context-ltv.png)

## Exemples {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```


---
description: Le suivi des balises permet de mesurer et de cibler des micro-emplacements à l’aide d’iBeacon et du Bluetooth basse énergie (Bluetooth Low Energy).
keywords: android ; library ; mobile ; sdk
seo-description: Le suivi des balises permet de mesurer et de cibler des micro-emplacements à l’aide d’iBeacon et du Bluetooth basse énergie (Bluetooth Low Energy).
seo-title: Suivi des balises
solution: Marketing Cloud, Analytics
title: Suivi des balises
topic: Développeur et mise en œuvre
uuid: 16 c 1 d 267-85 f 4-4 a 6 a-a 6 d 3-d 6 ffb 0 f 80 b 29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Suivi des balises {#beacon-tracking}

Le suivi des balises permet de mesurer et de cibler des micro-emplacements à l’aide d’iBeacon et du Bluetooth basse énergie (Bluetooth Low Energy).

Les données de balises suivantes sont envoyées à Analytics et à Target lorsque `trackBeacon` est appelé :

* `a.beacon.uuid` - Proximityuuid de la balise
* `a.beacon.major` : numéro majeur de la balise (par exemple, le numéro de la boutique)
* `a.beacon.minor` : numéro mineur de la balise (par exemple, un numéro unique dans une boutique)
* `a.beacon.prox` : valeurs 0 à 3 représentant la distance de l’utilisateur par rapport à la balise.

Ces valeurs ont la signification suivante :

* 0 = distance inconnue
* 1 = proximité immédiate
* 2 = proche
* 3 = lointain

Ces données de balise sont capturées dans les variables des solutions mobiles.

## Suivi des balises {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier Config à votre projet intellij IDEA ou Eclipse* dans [l'implémentation principale et le cycle de vie](/help/android/getting-started/dev-qs.md).

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Récupérez la position des balises.

   Plusieurs bibliothèques tierces sont disponibles pour numériser les balises Bluetooth Low Energy, selon le fabricant de la balise.
1. Une fois les informations de balise obtenues, vous pouvez utiliser l’appel suivant pour effectuer le suivi de l’emplacement :

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. Lorsque l’utilisateur quitte la proximité de la balise, effacez la balise actuelle :

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Outre les données de balises, vous pouvez envoyer des données contextuelles supplémentaires avec chaque appel `trackBeacon` :

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

Les valeurs de données contextuelles doivent être associées à des variables personnalisées dans les services Adobe Mobile :

![](assets/map-variable-context-ltv.png)


---
description: La fonctionnalité de prérécupération d’Adobe Target utilise les SDK Android Mobile pour récupérer le contenu des offres aussi peu de fois que possible en mettant en cache les réponses du serveur.
title: Prérécupération du contenu des offres dans Android
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
exl-id: 60fd9703-972b-4c2c-bf9c-86e1f59bfba5
source-git-commit: 5d44c09a18a557e934628533c4eefaa9e26aba42
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 92%

---

# Prérécupération du contenu des offres dans Android {#prefetch-offer-content-in-android}

La fonctionnalité de prérécupération d’Adobe Target utilise les SDK Android Mobile pour récupérer le contenu des offres aussi peu de fois que possible en mettant en cache les réponses du serveur.

Ce processus réduit le temps de chargement, empêche plusieurs appels réseau et permet à Adobe Target d’être informé de la mbox visitée par l’utilisateur de l’application mobile. Tout le contenu sera récupéré et mis en cache lors de l’appel de prérécupération. Ce contenu sera récupéré du cache pour tous les appels futurs contenant du contenu mis en cache pour le nom de mbox spécifié.

Le contenu de la prérécupération n’est pas conservé d’une exécution à l’autre. Il reste dans le cache tant que l’application est active ou jusqu’à ce que la méthode `clearPrefetchCache()` soit appelée.

>[!IMPORTANT]
>
>Les API de prérécupération de Target sont disponibles depuis la version 4.14.0 du SDK. Pour plus d’informations sur les restrictions des paramètres, voir [Paramètres d’entrée de lot](https://developers.adobetarget.com/api/#batch-input-parameters).

Dans le SDK version 4.14 ou ultérieure l’identifiant `environmentId``ADBMobileConfig.json`, si spécifié, est sélectionné dans le fichier lors de l’initialisation d’un appel mBox en lots TnT v2. Si aucun `environmentId` n’est spécifié dans ce fichier, aucun paramètre d’environnement n’est envoyé dans l’appel mBox en lots TnT, et l’offre est fournie pour l’environnement par défaut.

Par exemple :

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Méthodes de prérécupération {#section_05967F1F3A554B0FBC2C08A954554BDE}

Vous trouverez ci-dessous la liste des méthodes pouvant être utilisées pour la prérécupération dans Android :

* **prefetchContent**

   Envoie une demande de prérécupération avec une matrice d’emplacements au serveur Target configuré et renvoie l’état de la demande dans le rappel fourni.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Voici les paramètres pour cette méthode :

      * **targetPrefetchArray**

         Matrice de `TargetPrefetchObjects` contenant le nom et les paramètres mboxParameters de chaque emplacement Target à prérécupérer.

      * **profileParameters**

         Contient les clés et les valeurs des paramètres de profil à utiliser avec chaque prérécupération d’emplacement de cette demande.

      * **callback**

         Appelé une fois la prérécupération terminée. Renvoie `true` si la prérécupération a réussi et `false` si la prérécupération a échoué.

* **loadRequests**

   Exécute une demande par lot portant sur plusieurs emplacements de mbox spécifiés dans la matrice de demandes.  Chaque objet de la matrice contient une fonction de rappel qui est appelée lorsque le contenu est disponible pour son emplacement de mbox correspondant.

   >[!IMPORTANT]
   >
   >Si le contenu des emplacements demandés a déjà été mis en cache, il est renvoyé immédiatement dans le rappel fourni. Dans le cas contraire, le SDK envoie une demande de réseau aux serveurs Target afin de récupérer le contenu.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Voici les paramètres pour cette méthode :

      * **requestArray**

         Matrice de `TargetRequestObjects` contenant le nom, le contenu par défaut, les paramètres et la fonction de rappel de chaque emplacement à récupérer.

      * **profileParameters**

         Contient les clés et les valeurs des paramètres de profil à utiliser avec chaque prérécupération d’emplacement de cette demande.

* **clearPrefetchCache**

   Efface les données mises en cache par la fonctionnalité de prérécupération de Target.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void clearPrefetchCache();
      ```

   * Il n’existe aucun paramètre pour cette méthode.

* **createTargetRequestObject**

   Crée et renvoie une instance de `TargetRequestObject` avec les données fournies.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Crée et renvoie une instance de TargetPrefetchObject avec les données fournies.

   * Voici la syntaxe de cette méthode :

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Classes publiques {#section_A273E53F069E4327BBC8CE4910B37888}

Vous trouverez ci-dessous la liste des classes publiques qui prennent en charge la fonction de prérécupération dans Android :

### Référence de classe : TargetPrefetchObject

Encapsule le nom de la mbox et les paramètres utilisés pour la prérécupération de la mbox.

* **`name`**

   Nom de l’emplacement qui sera prérécupéré.
   * **Type** : String

* `mboxParameters`

   Collection de paires clé-valeur qui sera jointe en tant que `mboxParameters` pour cette demande de `TargetPrefetchObject`.
   * **Type** : Map`<String, Object>`

* **`orderParameters`**

   Collection de paires clé-valeur qui sera jointe à la mbox active sous le nœud order.
   * **Type** : Map`<String, Object>`

* **`productParameters`**

   Collection de paires clé-valeur qui sera jointe à la mbox active sous le nœud product.

   * **Type** : Map`<String, Object>`


### Référence de classe : TargetRequestObject

Cette classe encapsule le nom de mbox, le contenu par défaut, les paramètres de mbox et le rappel de renvoi utilisés pour les demandes d’emplacement Target.

* **`mboxName`**

   Nom de l’emplacement demandé.

   * **Type** : String

* **`mboxParameters`**

   Collection de paires clé-valeur qui sera jointe en tant que `mboxParameters` pour cette instance de `TargetRequestObject`.

   * **Type : Map`<String, Object>`**

* **`orderParameters`**

   Collection de paires clé-valeur qui sera jointe à la mbox active sous le nœud order.

   * **Type** : Map`<String, Object>`

* **`productParameters`**

   Collection de paires clé-valeur qui sera jointe à la mbox active sous le nœud product.

   * **Type** : Map`<String, Object>`

* **`defaultContent`**

   Valeur de chaîne renvoyée dans le rappel si le SDK ne parvient pas à récupérer le contenu à partir des serveurs Target.

   * **Type** : String

* **`callback`**

   Pointeur de fonction qui sera appelé lorsque le contenu de l’instance de `TargetRequestObject` donnée est disponible.

   * **Type** : Target.TargetCallback`<String>`


## Exemple de code {#section_BF7F49763D254371B4656E17953D520C}

Vous trouverez ci-dessous un exemple de procédure de prérécupération de contenu à l’aide des SDK Android :

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## Informations supplémentaires {#section_A454BAD1CD49423E86C71BAEE06125FD}

Informations supplémentaires concernant ces exemples :

* `ProductParameters` accepte uniquement les clés suivantes :

   * `id`
   * `categoryId`

* `OrderParameters` accepte uniquement les clés suivantes :

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` accepte une liste ArrayList de chaînes.

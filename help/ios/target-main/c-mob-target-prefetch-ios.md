---
description: La fonctionnalité de prérécupération d’Adobe Target utilise les SDK iOS Mobile pour récupérer le contenu des offres aussi peu de fois que possible en mettant en cache les réponses du serveur.
seo-description: La fonctionnalité de prérécupération d’Adobe Target utilise les SDK iOS Mobile pour récupérer le contenu des offres aussi peu de fois que possible en mettant en cache les réponses du serveur.
seo-title: Prérécupération du contenu des offres dans iOS
title: Prérécupération du contenu des offres dans iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Prérécupération du contenu des offres dans iOS {#prefetch-offer-content-in-ios}

La fonctionnalité de prérécupération d’Adobe Target utilise les SDK iOS Mobile pour récupérer le contenu des offres aussi peu de fois que possible en mettant en cache les réponses du serveur.

>[!IMPORTANT]
>
>Prefetch functionality in the Mobile SDKs for iOS is not supported for Auto Target, Auto Allocate, and Automated Personalization activity types in Adobe Target.

Ce processus réduit le délai de chargement, évite la multiplication des appels réseau et permet d’informer Adobe Target de la mbox que l’utilisateur de l’application mobile a été visitée. L’ensemble du contenu sera récupéré et mis en cache lors de l’appel de prérécupération. Ce contenu sera ensuite récupéré du cache pour tous les appels futurs contenant le contenu mis en cache pour cette mbox spécifique.

Le contenu de la prérécupération n’est pas conservé d’une exécution à l’autre. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

Dans le SDK version 4.14 ou ultérieure l’identifiant `environmentId``ADBMobileConfig.json`, si spécifié, est sélectionné dans le fichier lors de l’initialisation d’un appel mBox en lots TnT v2. Si aucun `environmentId` n’est spécifié dans ce fichier, aucun paramètre d’environnement n’est envoyé dans l’appel mBox en lots TnT, et l’offre est fournie pour l’environnement par défaut.

Par exemple :

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Prefetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Vous trouverez ci-dessous la liste des méthodes pouvant être utilisées pour la prérécupération dans iOS :

* **targetPrefetchContent**

   Envoie une demande de prérécupération avec une matrice d’emplacements au serveur Target configuré et renvoie l’état de la demande dans le rappel fourni.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Here are the parameters for this method:

      * **`targetPrefetchArray`**

         Matrice de `TargetPrefetchObjects` contenant le nom et les paramètres mboxParameters de chaque emplacement Target à prérécupérer.

      * **`profileParameters`**

         Contient les clés et les valeurs des paramètres de profil à utiliser avec chaque prérécupération d’emplacement de cette demande.

      * **`callback`**

         Appelé une fois la prérécupération terminée. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

   Exécute une demande par lot portant sur plusieurs emplacements de mbox spécifiés dans la matrice de demandes. Chaque objet de la matrice contient une fonction de rappel qui est appelée lorsque le contenu est disponible pour son emplacement de mbox correspondant.

   >[!IMPORTANT]
   >
   >Si le contenu des emplacements demandés est déjà mis en cache, il est renvoyé immédiatement dans le rappel fourni. Dans le cas contraire, le SDK envoie une demande de réseau aux serveurs Target afin de récupérer le contenu.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Here are the parameters for this method:

      * **`requests`**

         Matrice de `TargetRequestObjects` contenant le nom, le contenu par défaut, les paramètres et la fonction de rappel de chaque emplacement à récupérer.

      * **`profileParameters`**

         Contient les clés et les valeurs des paramètres de profil à utiliser avec chaque prérécupération d’emplacement de cette demande.

* **targetPrefetchClearCache**

   Efface les données mises en cache par la fonctionnalité de prérécupération de Target.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * Il n’existe aucun paramètre pour cette méthode.

* **targetRequestObjectWithName**

   Crée et renvoie une instance de `TargetRequestObject` avec les données fournies.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * There are no parameters for this method.

* **createTargetPrefetchObject**

   Crée et renvoie une instance de `TargetPrefetchObject` avec les données fournies.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Vous trouverez ci-dessous la liste des classes publiques qui prennent en charge la fonction de prérécupération dans iOS :

### Référence de classe : TargetPreFetchObject

Encapsule le nom de la mbox et les paramètres utilisés pour la prérécupération de la mbox.

* **`name`**

   Name for the location/mbox you want to retrieve.

   * **Type** : NSString*

* **`mboxParameters`**

   Dictionnaire facultatif qui contient les paires clé-valeur des paramètres de mbox.

   * **Type** : NSDictionary*

* **`orderParameters`**

   Dictionnaire qui contient les paires clé-valeur des paramètres de commande.

   * **Type** : NSDictionary*

* **`productParameters`**

   Dictionnaire facultatif qui contient les paires clé-valeur des paramètres de produit.

   * **Type** : NSDictionary*

### Référence de classe : TargetRequestObject

Cette classe encapsule le nom de mbox, le contenu par défaut, les paramètres de mbox et le rappel de renvoi utilisés pour les demandes d’emplacement Target.

* **`name`**

   Nom de l’emplacement demandé.

   * **Type** : NSString*

* **`mboxParameters`**

   Valeur NSString qui représente le nom de l’emplacement/la mbox que vous souhaitez récupérer.

   * **Type** : NSString*

* **`defaultContent`**

   Contenu par défaut qui sera renvoyé si les serveurs Target ne sont pas accessibles.

   * **Type** : NSString*

* **`callback`**

   En cas de demande par lot d’emplacements Target, une fonction de rappel est appelée lorsque le contenu est disponible pour l’emplacement correspondant.

   * **Type** : fonction

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Vous trouverez ci-dessous un exemple de procédure de prérécupération de contenu à l’aide des SDK iOS :

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Vous trouverez ci-dessous un exemple de demande `loadRequest` par lot à l’aide des SDK iOS :

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
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

* `purchasedProducts` accepte un tableau de chaînes.
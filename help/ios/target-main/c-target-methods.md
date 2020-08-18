---
description: Cette section répertorie les méthodes Adobe Target fournies par la bibliothèque iOS.
seo-description: Cette section répertorie les méthodes Adobe Target fournies par la bibliothèque iOS.
seo-title: Méthodes Target pour iOS pour Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Méthodes Target pour iOS
topic: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '656'
ht-degree: 100%

---


# Méthodes de ciblage pour iOS {#target-methods}

Cette section répertorie les méthodes Adobe Target fournies par la bibliothèque iOS.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform. Un préfixe est ajouté aux méthodes selon la solution. Par exemple, les méthodes sont précédées du préfixe `target` target.

>[!TIP]
>
>Les mesures de cycle de vie sont envoyées sous la forme de paramètres à chaque chargement de mbox. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md). Si vous envoyez des requêtes Target dans la méthode `didFinishLaunching` déléguée, ajoutez un appel `[ADBMobile trackAction:data:]` ou `[ADBMobile trackState:data:]` avant le code de mise en œuvre Target. Ainsi, les requêtes Target contiennent les données de cycle de vie complètes.

## Référence de classe : ADBTargetLocationRequest

### Propriétés

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Constantes de chaîne

>[!TIP]
>
>Les constantes suivantes facilitent la définition des clés pour les paramètres personnalisés.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Si vous utilisez un SDK **antérieur** à la version 4.14.0, voir [Paramètres d’entrée](https://developers.adobetarget.com/api/#input-parameters) pour les restrictions des paramètres.
   >
   >
* Si vous utilisez un SDK version 4.14.0 **ou version supérieure**, voir [Paramètres d’entrée de lot](https://developers.adobetarget.com/api/#batch-input-parameters) pour les restrictions des paramètres.


### Méthodes

* **targetLoadRequest:&#x200B;callback**

   Envoie request au serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un bloc `callback`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   Envoie la demande à votre serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Renvoie : S/O

   * Voici les paramètres pour cette méthode :

      * **`name`**

         Nom de la mbox/l’emplacement Target que vous voulez récupérer.

         * **Type** : NSString*
      * **`defaultContent`**

         Valeur renvoyée dans le rappel si le serveur Target n’est pas accessible ou si l’utilisateur n’est pas admissible pour la campagne.

         * **Type** : NSString*
      * **`profileParameters`**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;profileParameters&quot; dans la demande à Target.

         * **Type** : NSDictionary*
      * **`orderParameters`**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;order&quot; dans la demande à Target.

         * **Type** : NSDictionary
      * **`mboxParameters`**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;mboxParameters&quot; dans la demande à Target.

         * **Type** : NSDictionary*
      * **`requestLocationParameters`**

         Les valeurs de ce dictionnaire seront placées dans l’objet &quot;requestLocation&quot; dans la demande à Target.

         **Type** : NSDictionary*

      * **`callback`**

         Cette méthode est appelée avec le contenu de l’offre depuis le serveur Target. Lorsque le serveur Target est inaccessible ou que l’utilisateur ne répond pas aux critères de la campagne, defaultContent est renvoyé.
      **Type** : fonction

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Pour plus d’informations sur l’API Target sous-jacent, voir [Développeurs Adobe Target](https://docs.adobe.com/dev/products/target/reference/delivery.html).







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   Envoie request à votre serveur Target configuré et renvoie la valeur de chaîne de l’offre générée dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   Crée une `ADBTargetLocationRequest`.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   Constructeur de commodité permettant de créer un objet ADBTargetLocationRequest avec les paramètres donnés.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Renvoie l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Définit l’identifiant tiers.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Efface les cookies de ciblage de l’application.

   >[!TIP]
   >
   >Depuis la version 4.10.0 du SDK, Target n’utilise plus les cookies. Cette méthode permet de réinitialiser thirdPartyID et sessionID.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Renvoie le PcID.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Renvoie SessionID.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Exemple

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```

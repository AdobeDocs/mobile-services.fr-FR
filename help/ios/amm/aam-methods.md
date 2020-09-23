---
description: Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.
seo-description: Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.
seo-title: Méthodes Audience Manager
solution: Experience Cloud,Analytics
title: Méthodes Audience Manager
topic: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 80%

---


# Méthodes Audience Manager{#audience-manager-methods}

Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform. Le préfixe précédant les méthodes varie selon la solution. Les méthodes Audience Manager sont précédées du préfixe « `audience`audience ».

Si Audience Manager est configuré dans votre fichier JSON, un signal contenant les mesures de cycle de vie est envoyé avec `application:didFinishLaunchingWithOptions:`.

* **audienceVisitorProfile**

   Renvoie le dernier profil du visiteur obtenu ou renvoie `null` lorsqu’aucun signal n’a été envoyé. Le profil du visiteur est enregistré dans `NSUserDefaults` pour un accès facile à l’échelle de plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Voici l’exemple de code pour ce menu :

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   Renvoie le DPID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   Renvoie le DPUUID en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   Définit les DPID et DPUUID. Une fois définies, les deux sont ajoutées à chaque signal.

   * L’ID de fournisseur de **données (DPID)** est l’ID de partenaire de données qui est attribué par Audience Manager.
   * L’ID utilisateur unique du fournisseur de **données (DPUUID)** est l’ID unique du fournisseur de données pour l’utilisateur.

      >[!IMPORTANT]
      >
      >Avant la version 4.13.x, le DPUUID n’était pas codé automatiquement. À partir de la version 4.13.x, le SDK commence par décoder la valeur transmise, puis réencoder cette valeur. Ce processus permet de s’assurer que le SDK ne rompt pas la compatibilité ascendante.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Réinitialise l’UUID d’Audience Manager et purge le profil du visiteur actuel.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(void) audienceReset;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Envoie à la gestion de l’audience un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Exemple

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```

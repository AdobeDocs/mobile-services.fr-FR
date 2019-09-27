---
description: Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.
seo-description: Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.
seo-title: Méthodes Audience Manager
solution: Marketing Cloud,Analytics
title: Méthodes Audience Manager
topic: Développeur et mise en œuvre
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

Cette section répertorie les méthodes Audience Manager fournies par la bibliothèque iOS.

The SDK currently supports multiple Adobe Experience Cloud Solutions, including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service. Le préfixe précédant les méthodes varie selon la solution. Les méthodes  Manager sont précédées du préfixe « `audience`audience ».

Si Audience Manager est configuré dans votre fichier JSON, un signal contenant les mesures de cycle de vie est envoyé avec `application:didFinishLaunchingWithOptions:`.

* **audienceVisitorProfile**

   Renvoie le dernier profil du visiteur obtenu ou renvoie `null` lorsqu’aucun signal n’a été envoyé. Le profil du visiteur est enregistré dans `NSUserDefaults` pour un accès facile à l’échelle de plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Voici un exemple de code pour ce menu :

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

   Définit les DPID et DPUUID. Une fois définis, les deux identifiants sont ajoutés à chaque signal.

   * L’**identifiant du fournisseur de données (DPID)** est l’identifiant du partenaire fournisseur de données affecté par Audience Manager.
   * L’**identifiant de l’utilisateur unique du fournisseur de données (DPUUID)** est l’identifiant unique du fournisseur de données pour l’utilisateur.

      >[!IMPORTANT]
      >
      >Avant la version 4.13.x, le DPUUID n’était pas automatiquement codé. À compter de la version 4.13.x, le SDK commence par décoder la valeur transmise, puis recode cette valeur. Ce processus permet au SDK de préserver la rétrocompatibilité.

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

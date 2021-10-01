---
description: Vous trouverez ci-après les méthodes du service d’identification Adobe Experience Platform fournies par la bibliothèque iOS.
solution: Experience Cloud,Analytics
title: Méthodes de services d’identification Adobe Experience Platform
topic-fix: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
exl-id: 82a246fc-f679-4fa5-b9c0-dc909a7e7d93
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 96%

---

# Méthodes de services d’identification Adobe Experience Platform {#experience-cloud-id-service-methods}

Vous trouverez ci-après les méthodes du service d’identification Adobe Experience Platform fournies par la bibliothèque iOS.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification des visiteurs d’Experience Cloud.

Un préfixe est attribué aux méthodes selon la solution. Les méthodes Experience Cloud ID sont précédées du préfixe `visitor`. Pour plus d’informations, voir [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL `*`)visitorAppendToURL:(nullable NSURL `*`)url;**

   Ajoute les données du visiteur Adobe à une chaîne d’URL en vue d’une utilisation dans la bibliothèque JavaScript Adobe. Pour utiliser cette méthode, il vous faut le SDK mobile version 4.12 ou ultérieure. Pour plus d’informations, voir [appendVisitorIDsTo](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/appendvisitorid.html?lang=fr) dans la documentation du service Adobe Experience Cloud Identity.

   >[!IMPORTANT]
   >
   >Cette méthode peut entraîner un appel de blocage réseau. N’appelez pas cette méthode pour des fils soumis à des contraintes de temps.

   * Entrée : `URL<NSURL>`
Chaîne URL à laquelle les données du visiteur seront ajoutées.
   * `URL<NSURL>`
Chaîne comportant les informations sur les visiteurs ajoutées.

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Récupère l’Experience Cloud ID du service d’identification.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >Cette méthode peut provoquer un appel réseau bloquant et **ne doit pas** être appelée depuis un fil d’interface utilisateur.

* **visitorSyncIdentifiers:**

   Avec l’Experience Cloud ID, vous pouvez définir d’autres identifiants de client qui peuvent être associés à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour un même visiteur, ainsi qu’un identifiant de type client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants `setCustomerIDs` dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Synchronise les identifiants fournis au service d’identification. Transmettez `authState` sous la forme d’une des valeurs suivantes :

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Synchronise le type d’identifiant et la valeur fournis au service d’identification. Transmettez `authState` sous la forme d’une des valeurs suivantes :

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Voici la syntaxe de cette méthode :

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Récupère une matrice d’objets `ADBVisitorID` en lecture seule.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   Introduite dans la version 4.16.0, cette méthode renvoie une chaîne correctement formée contenant des variables URL du service d’identification des visiteurs. Pour plus d’informations sur l’utilisation de cette méthode [Méthodes de services d’identification Adobe Experience Platform](/help/ios/reference/hybrid-app.md).

   * Voici la syntaxe de cette méthode :

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID interface {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Méthodes publiques :**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum  {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

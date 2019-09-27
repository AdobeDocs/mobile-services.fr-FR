---
description: Voici les méthodes du service d’identité Adobe Experience Platform fournies par la bibliothèque iOS.
seo-description: Voici les méthodes du service d’identité Adobe Experience Platform fournies par la bibliothèque iOS.
seo-title: Adobe Experience Platform Identity Service methods
solution: Marketing Cloud,Analytics
title: Adobe Experience Platform Identity Service methods
topic: Développeur et mise en œuvre
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Méthodes d’Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Here are the Adobe Experience Platform Identity Service methods that are provided by the iOS library.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification des visiteurs d’Experience Cloud.

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. Pour plus d’informations, voir [Activation de l’Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(NSURL nullable`*`)visitorAppendToURL:(NSURL nullable`*`)url;**

   Ajoute les données du visiteur Adobe à une chaîne d’URL en vue d’une utilisation dans la bibliothèque JavaScript Adobe. To use this method, you must have Mobile SDK version 4.12 or higher. Pour obtenir plus d’informations, voir [Ajout de la fonction d’application d’assistance de l’identifiant visiteur](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Cette méthode peut provoquer un appel réseau de blocage. N’appelez pas cette méthode pour des fils soumis à des contraintes de temps.

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
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
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Avec l’Experience Cloud ID, vous pouvez définir des identifiants de client supplémentaires pouvant être associés à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour un même visiteur, ainsi qu’un identifiant de type client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants `setCustomerIDs` dans la bibliothèque JavaScript.

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

   Synchronise le type d’identifiant et la valeur fournis au service d’identification. Pass in the `authState` one of the following values:

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

   Introduite dans la version 4.16.0, cette méthode renvoie une chaîne correctement formée contenant des variables URL du service d’identification des visiteurs. For more information about how this method is used, see Adobe Experience Platform Identity Service methods.[](/help/ios/reference/hybrid-app.md)

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

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```


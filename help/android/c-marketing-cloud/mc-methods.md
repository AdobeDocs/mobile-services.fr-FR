---
description: Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.
keywords: android ; library ; mobile ; sdk
seo-description: Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.
seo-title: Méthodes du service d'identité Adobe Experience Platform
solution: Marketing Cloud, Analytics
title: Méthodes du service d'identité Adobe Experience Platform
topic: Développeur et mise en œuvre
uuid: c 5107 a 7 e -273 b -4 f 71-8738-4 c 603479 b 24 c
translation-type: tm+mt
source-git-commit: a54a969bb6abedfeb0fc20276d260664b68c1d66

---


# Méthodes du service d'identité Adobe Experience Platform{#experience-cloud-id-service-methods}

Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud], notamment Analytics, Target, Audience Manager et le service d'identité Adobe Experience Platform.

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Ajoute les données des visiteurs Adobe à une chaîne d’URL pour utilisation avec la bibliothèque JavaScript d’Adobe. Vous devez disposer de la version 4.12 ou supérieure du SDK Mobile pour utiliser cette méthode. Pour obtenir plus d’informations, voir [Ajout de la fonction d’application d’assistance de l’identifiant visiteur](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[! IMPORTANT]
   >
   >Cette méthode peut entraîner un blocage réseau de blocage. N’appelez pas cette méthode pour des fils soumis à des contraintes de temps.

   * Voici la syntaxe de cette méthode :

      ```java
      URL java.lang.String  
      ```

      Chaîne d’URL requise à laquelle les informations sur les visiteurs sont ajoutées.

   * Voici l’exemple de code pour cette méthode :

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Récupère l’Experience Cloud ID auprès du service d’identification des visiteurs.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Avec l’Experience Cloud ID, vous pouvez définir des identifiants de client supplémentaires pouvant être associés à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour le même visiteur, ainsi qu’un identifiant de type Client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants `setCustomerIDs` dans la bibliothèque JavaScript.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **Syncidentifier**

   Synchronise la valeur et le type d’identifiant fournis avec le service d’identification des visiteurs.

   Transmettez `authenticationState` sous la forme d’une des valeurs suivantes :

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Voici la syntaxe de cette méthode :

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Synchronise les identifiants fournis au service d’identification.

   Transmettez `authenticationState` sous la forme d’une des valeurs suivantes :
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Voici la syntaxe de cette méthode :

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Récupère une liste d’objets `ADBVisitorID` en lecture seule.

   * Voici la syntaxe de cette méthode :

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **Geturlvariablesasync**

   Introduit dans la version 4.16.0, cette méthode renvoie une chaîne correctement formée qui contient les variables URL du service d'identification des visiteurs. Pour plus d'informations sur la manière dont cette méthode est utilisée, voir [Méthodes du service d'identité Adobe Experience Platform](/help/android/reference/hybrid-app.md).

   * Voici la syntaxe de cette méthode :

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```

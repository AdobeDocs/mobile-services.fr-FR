---
description: Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.
keywords: android;library;mobile;sdk
seo-description: Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.
seo-title: Méthodes de services d’identification Adobe Experience Platform
solution: Experience Cloud,Analytics
title: Méthodes de services d’identification Adobe Experience Platform
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---


# Méthodes de services d’identification Adobe Experience Platform {#experience-cloud-id-service-methods}

Voici les méthodes du service d’Experience Cloud ID fournies par la bibliothèque Android.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target, Audience Manager, ainsi que le service d’identification Adobe Experience Platform.

Un préfixe est attribué aux méthodes selon la solution. Par exemple, les méthodes d’Experience Cloud ID sont affectées du préfixe `visitor`. Pour plus d’informations, voir [Service d’Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Ajoute les données du visiteur Adobe à une chaîne d’URL en vue d’une utilisation dans la bibliothèque JavaScript Adobe. Pour utiliser cette méthode, vous devez disposer du SDK Mobile 4.12+. Pour obtenir plus d’informations, voir [Ajout de la fonction d’application d’assistance de l’identifiant visiteur](https://docs.adobe.com/content/help/fr-FR/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Cette méthode peut entraîner un appel de blocage réseau. N’appelez pas cette méthode pour des fils soumis à des contraintes de temps.

   * Voici la syntaxe de cette méthode :

      ```java
      public static String appendToURL(final String URL) 
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
      >Cette méthode peut provoquer un appel réseau bloquant et **ne doit pas** être appelée depuis un fil d’interface utilisateur.

* **syncIdentifiers**

   Avec l’Experience Cloud ID, vous pouvez définir d’autres identifiants de client qui peuvent être associés à chaque visiteur. L’API visiteur accepte plusieurs identifiants de client pour un même visiteur, ainsi qu’un identifiant de type client, afin de séparer la portée des différents identifiants de client. Cette méthode correspond aux identifiants `setCustomerIDs` dans la bibliothèque JavaScript.

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

* **syncIdentifier**

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

* **getUrlVariablesAsync**

   Introduite dans la version 4.16.0, cette méthode renvoie une chaîne correctement formée contenant des variables URL du service d’identification des visiteurs. Pour plus d’informations sur l’utilisation de cette méthode [Méthodes de services d’identification Adobe Experience Platform](/help/android/reference/hybrid-app.md).

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

## Méthodes publiques {#section_8AC744B431A3438C9B45629CA3EA0F51}

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

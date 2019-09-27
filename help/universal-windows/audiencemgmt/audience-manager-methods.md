---
description: Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.
seo-description: Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.
seo-title: Méthodes d’Audience Manager
solution: Marketing Cloud,Analytics
title: Méthodes d’Audience Manager
topic: Développeur et mise en œuvre
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

Si le gestionnaire d’audiences est configuré dans votre fichier JSON, un signal contenant des mesures de cycle de vie est envoyé avec votre accès au cycle de vie.

* **GetVisitorProfile (winJS : getVisitorProfile)**

   Renvoie le dernier profil du visiteur obtenu. Renvoie `null` si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `SharedPreferences` pour un accès facile à l’échelle de plusieurs lancements de l’application.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS : getDpid)**

   Renvoie le DPID en cours.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid (winJS : getDpuuid)**

   Renvoie le DPUUID en cours.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid (winJS : setDpidAndDpuuid)**

   Définit les DPID et DPUUID. Si les DPID et DPUUID sont définis, ils sont envoyés avec chaque signal.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS : signalWithData)**

   Envoie à la gestion de l’audience un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      

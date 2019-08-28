---
description: Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.
seo-description: Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.
seo-title: Méthodes Audience Manager
solution: Marketing Cloud, Analytics
title: Méthodes Audience Manager
topic: Développeur et mise en œuvre
uuid: efbe 8 f 33-7 f 53-40 a 6-b 7 aa-a 36 ac 718 c 047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

Liste des méthodes Audience Manager fournies par la bibliothèque Plateforme Windows universelle.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

Si Audience Manager est configuré dans votre fichier JSON, un signal qui contient des mesures de cycle de vie est envoyé avec votre accès au cycle de vie.

* **Getvisitorprofile (winjs : Getvisitorprofile)**

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

* **Getdpid (winjs : Getdpid)**

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

* **Getdpuuid (winjs : Getdpuuid)**

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

* **Setdpidanddpuuid (winjs : Setdpidanddpuuid)**

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

* **Signalwithdata (winjs : Signalwithdata)**

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
      

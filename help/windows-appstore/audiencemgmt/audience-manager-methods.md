---
description: Liste des méthodes Audience Manager fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.
seo-description: Liste des méthodes Audience Manager fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.
seo-title: Méthodes Audience Manager
solution: Marketing Cloud, Analytics
title: Méthodes Audience Manager
topic: Développeur et mise en œuvre
uuid: e 39 c 9 c 3 e-fd 53-4 b 46-8 fff -88101 a 064 a 9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Liste des méthodes Audience Manager fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes Audience Manager est « AudienceManager ».

>[!NOTE]
>
>Lorsque vous utilisez des méthodes winmd à partir de winjs (JavaScript), toutes les méthodes comportent automatiquement leur première lettre.

Si Audience Manager est configuré dans le fichier JSON, un signal qui contient des mesures de cycle de vie est envoyé avec l’accès de cycle de vie.

* **Getvisitorprofile (winjs : Getvisitorprofile)**

   Renvoie le dernier profil du visiteur obtenu. Renvoie `null` si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `SharedPreferences` pour un accès facile à l’échelle de plusieurs lancements de l’application.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
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

   Envoie à Audience Manager un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel de bloc.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```


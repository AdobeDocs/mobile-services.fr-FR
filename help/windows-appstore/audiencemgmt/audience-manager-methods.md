---
description: Liste des méthodes d’Audience Manager fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-description: Liste des méthodes d’Audience Manager fournies par la bibliothèque Windows 8.1 Universal App Store.
seo-title: Méthodes Audience Manager
solution: Experience Cloud,Analytics
title: Méthodes Audience Manager
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Méthodes Audience Manager {#audience-manager-methods}

Liste des méthodes d’Audience Manager fournies par la bibliothèque Windows 8.1 Universal App Store.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Cible et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Les méthodes d’Audience Manager comportent le préfixe &quot;AudienceManager&quot;.

>[!NOTE]
>
>Lorsque vous consommez des méthodes winmd de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre minuscule.

Si le gestionnaire d’audiences est configuré dans votre fichier JSON, un signal contenant des mesures de cycle de vie est envoyé avec votre accès de cycle de vie.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Renvoie le dernier profil du visiteur obtenu. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

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

* **GetDpuuid (winJS: getDpuuid)**

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

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Définit les DPID et DPUUID. Si les DPID et DPUUID sont définis, ils seront envoyés avec chaque signal.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Envoie à l’Audience Manager un signal avec des caractéristiques et obtient les segments correspondants renvoyés dans un rappel de bloc.

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


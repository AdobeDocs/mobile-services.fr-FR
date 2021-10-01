---
description: Liste des méthodes d’Audience Manager fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.
solution: Experience Cloud,Analytics
title: Méthodes Audience Manager
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Méthodes Audience Manager {#audience-manager-methods}

Liste des méthodes d’Audience Manager fournies par la bibliothèque Boutique d’applications Windows 8.1 universelle.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Target et Audience Manager. Un préfixe est ajouté aux méthodes selon la solution. Le préfixe des méthodes d’Audience Manager est &quot;AudienceManager&quot;.

>[!NOTE]
>
>Lorsque vous utilisez des méthodes winmd à partir de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre en minuscules.

Si audience Manager est configuré dans votre fichier JSON, un signal contenant les mesures de cycle de vie est envoyé avec votre accès de cycle de vie.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Renvoie le dernier profil du visiteur obtenu. Renvoie `null` si aucun signal n’a encore été envoyé. Le profil du visiteur est enregistré dans `SharedPreferences` pour un accès facile à l’échelle de plusieurs lancements de votre application.

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

   Envoie à l’Audience Manager un signal avec des caractéristiques et récupère les segments correspondants renvoyés dans un rappel de bloc.

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

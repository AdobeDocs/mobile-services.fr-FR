---
description: Liste des méthodes d'Audience Manager fournies par la bibliothèque de plateformes Windows universelles.
seo-description: Liste des méthodes d'Audience Manager fournies par la bibliothèque de plateformes Windows universelles.
seo-title: Méthodes Audience Manager
solution: Experience Cloud,Analytics
title: Méthodes Audience Manager
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---

# Méthodes Audience Manager {#audience-manager-methods}

Liste des méthodes d&#39;Audience Manager fournies par la bibliothèque de plateformes Windows universelles.

Le SDK prend actuellement en charge plusieurs solutions Adobe Experience Cloud, notamment Analytics, Cible et Audience Manager. Les méthodes sont préfixées en fonction de la solution. Les méthodes d&#39;Audience Manager sont précédées du préfixe `AudienceManager`.

>[!TIP]
>
>Lorsque vous utilisez des méthodes `winmd` de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre avec un caractère minuscule.

Si le gestionnaire d’audiences est configuré dans votre fichier JSON, un signal contenant des mesures de cycle de vie est envoyé avec votre accès de cycle de vie.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Renvoie le dernier profil du visiteur obtenu. Renvoie `null` si aucun signal n&#39;a encore été envoyé. Le profil du visiteur est enregistré dans `SharedPreferences` pour un accès facile à plusieurs lancements de votre application.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

* **SignalWithData (winJS : signalWithData)**

   Envoie à la gestion des audiences un signal avec des caractéristiques et obtient les segments correspondants renvoyés dans un rappel de bloc.

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
      ```

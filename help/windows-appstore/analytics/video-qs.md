---
description: Informations relatives aux analyses vidéo.
seo-description: Informations relatives aux analyses vidéo.
seo-title: Analyses de vidéos
solution: Experience Cloud,Analytics
title: Analyses de vidéos
topic: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 71%

---


# Analyses de vidéos {#video-analytics}

Informations relatives aux analyses vidéo.

Les mesures vidéo sont décrites en détail dans le guide [Mesure audio et vidéo en Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/media-analytics/using/media-overview.html/) . Le processus général de mesure vidéo est très similaire sur toutes les plateformes AppMeasurement. Cette section de début rapide fournit un aperçu de base des tâches des développeurs ainsi que des exemples de code.

Le tableau suivant répertorie les données multimédias envoyées à Analytics. Utilisez des règles de traitement pour mapper les données contextuelles à une variable Analytics.

* **a.media.name**

   (Obligatoire) Collecte le nom de la vidéo, tel qu&#39;il est spécifié dans l&#39;implémentation, lorsqu&#39;un visiteur vue la vidéo d&#39;une manière ou d&#39;une autre.Vous pouvez ajouter des classifications pour cette variable.

   (**Optional**) The Custom Insight variable provides video pathing information.

   * Type de variable : eVar
   * Délai d’expiration par défaut : Visite
   * Custom Insight (s.prop, utilisée pour le cheminement vidéo)

* **a.media.name**

   (Facultatif) Fournit des informations de cheminement vidéo. Le cheminement doit être activé par ClientCare pour cette variable.

   Type d’événement : Insight personnalisé (s.prop)

   * Type de variable : Insight personnalisé (s.prop)

* **a.media.segment**

   (Obligatoire) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo. Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   La méthode de collecte de données vidéo par défaut collecte les données aux points suivants :

   * lorsque la vidéo démarre (lecture) ;
   * lorsque le segment débute ;
   * lorsque la vidéo prend fin (arrêt).

   Analytics comptabilise la première vue du segment au début du segment, lorsque le visiteur commence à regarder. Les vues des segments suivants démarrent au début des segments.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue


* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les accès envoyés par mesure vidéo se voient attribuer un type de contenu &quot;vidéo&quot;. Cette variable ne doit pas être réservée exclusivement au suivi vidéo. La présence d’un autre type de contenu de rapport de contenu à l’aide de cette même variable vous permet d’analyser la répartition des visiteurs entre les différents types de contenu. Par exemple, vous pouvez baliser les types de contenu en utilisant des valeurs telles que « article » ou « page de produits » à l’aide de cette variable. Du point de vue des mesures vidéo, le type de contenu vous permet d’identifier les visiteurs vidéo et de calculer les taux de conversion vidéo.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue

* **a.media.timePlayed**

   Compte le temps de lecture vidéo passé, en secondes, depuis le dernier processus de collecte de données (requêtes d’images).

   * Type de variable : Evénement
   * Type : compteur

* **a.media.view**

   Indique qu’un visiteur a visionné une partie d’une vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée, ni la partie visionnée.

   * Variable : Événement
   * Type : compteur

* **a.media.segmentView**

   Indique qu’un visiteur a visionné une partie d’un segment de vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée, ni la partie visionnée.

   * Type de variable : Evénement
   * Type : compteur

* **a .media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et les autres flux qui n’ont pas de fin définie, vous pouvez spécifier un point personnalisé pour mesurer la fin. Par exemple, après un temps de lecture spécifique.

   * Type de variable : Evénement
   * Type : compteur


## Configuration des paramètres multimédias {#section_929945D4183C428AAF3B983EFD3E2500}

Configurez un objet `MediaSettings` avec les paramètres que vous voulez utiliser pour effectuer le suivi de la vidéo :

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Suivi des événements du lecteur {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Pour mesurer la lecture de vidéos, appelez les méthodes `Play`, `Stop`, et `Close` aux moments opportuns. Par exemple, lorsque le lecteur est en pause : `Stop`. `Play` est appelé lorsque la lecture démarre ou reprend.

## Classes {#section_16838332727348F990305C0C6B0D795C}

### Classe : MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## Références pour les méthodes et classes de mesure d’éléments multimédias {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Renvoie un objet `MediaSetting` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Renvoie un objet `MediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Open (winJS: open)**

   Effectue le suivi d&#39;un média ouvert à l&#39;aide des paramètres définis dans `settings`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Close (winJS : close)**

   Effectue le suivi de la fermeture d&#39;un média pour l&#39;élément média nommé *nom*.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS : play)**

   Effectue le suivi d&#39;une lecture multimédia pour l&#39;élément multimédia nommé *`name`* au *décalage* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Complete (winJS : complete)**

   Marque manuellement l’élément multimédia comme terminé au décalage *offset* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stop (winJS: stop)**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage *offset* donné.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Cliquez sur (winJS: click)**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS : track)**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.track("mediaName", null);
      ```


---
description: Informations relatives aux analyses de vidéos.
seo-description: Informations relatives aux analyses de vidéos.
seo-title: 'Chemin '
solution: Marketing Cloud, Analytics
title: 'Chemin '
topic: Développeur et mise en œuvre
uuid: f 45 dac 3 b-cd 2 e -4 fba-a 3 b 2-c 243640 ecfa 4
translation-type: tm+mt
source-git-commit: 1c0b7dadc28f772e903baa8605016e70f05081d7

---


# Chemin    {#video-analytics}

Informations relatives aux analyses de vidéos.

Video measurement is described in detail in the [Measuring video and audio in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guide. Le processus général de mesure vidéo se ressemble dans toutes les plates-formes AppMeasurement. Cette section de démarrage rapide donne une vue d’ensemble des tâches du développeur et fournit des exemples de code.

Le tableau suivant répertorie les données multimédias envoyées à Analytics. Utilisez les règles de traitement pour mapper les données contextuelles à une variable Analytics.

* **a.media.name**

   (**Required**) Collects the name of the video, as specified in the implementation, when a visitor views the video in some way.You can add classifications for this variable.

   (**Facultatif**) La variable Insight personnalisé fournit des informations sur le cheminement vidéo.

   * Type de variable : Evar
   * Délai d’expiration par défaut : Visite
   * Insight personnalisé (s.prop, utilisé pour le cheminement vidéo)

* **a.media.name**

   (**Facultatif)** Fournit des informations de cheminement vidéo. Le cheminement doit être activé par le service à la clientèle pour cette variable.

   * Type d’événement : Insight personnalisé (s.prop).
   * Type de variable : Custom Insight (s. prop)

* **a.media.segment**

   (**Obligatoire**) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo.

   Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segments eVar.

   La méthode par défaut de collecte de données est réalisée aux points suivants : le démarrage de la vidéo (play), le début du segment et la fin de la vidéo (stop). Analytics compte l’affichage du premier segment au début du segment, lorsque le visiteur commence la lecture. Les affichages de segments suivants commencent au démarrage du segment.

   * Type de variable : Evar
   * Délai d’expiration par défaut : page vue

* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les envois d’accès par mesure vidéo se voient attribuer un type de contenu « vidéo ». Cette variable ne doit pas être exclusivement réservée au suivi vidéo. Les autres types de contenu des rapports de contenu utilisant la même variable permettent d’analyser la distribution des visiteurs par rapport aux différents types de contenu. Par exemple, vous pouvez baliser les types de contenu en utilisant des valeurs telles que « article » ou « page de produits » à l’aide de cette variable.

   Du point de vue des mesures vidéo, le type de contenu permet d’identifier les visiteurs de vidéos et donc de calculer les taux de conversion vidéo.

   * Type de variable : Evar
   * Délai d’expiration par défaut : page vue

* **a.media.timePlayed**

   Compte le temps de lecture vidéo passé, en secondes, depuis le dernier processus de collecte de données (requêtes d’images).

   * Type de variable : Evénement
   * Type : compteur

* **a.media.view**

   Indique qu’un visiteur a visionné une partie d’une vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardé (ni la partie visionnée).

   * Type de variable : Evénement
   * Type : compteur

* **a.media.segmentView**

   Indique qu’un visiteur a visionné une partie d’un segment de vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée (ni la partie visionnée).

   * Type de variable : Evénement
   * Type : compteur

* **a .media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et les autres flux qui n’ont pas de fin définie, vous pouvez spécifier un point personnalisé pour mesurer la fin. Par exemple, après un temps de lecture spécifique.

   * Type de variable : Evénement
   * Type : compteur

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configurez un objet `MediaSettings` avec les paramètres que vous voulez utiliser pour effectuer le suivi de la vidéo :

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. Par exemple, lorsque le lecteur est en pause : `Stop`. `Play` est appelé lorsque la lecture démarre ou reprend.

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

### Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **Settingswith (winjs : Settingswith)**

   Renvoie un objet `MediaSettings` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **Adsettingswith (winjs : Adsettingswith)**

   Renvoie un objet `MediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **Open (winjs : open)**

   Effectue le suivi d’un média open en utilisant les paramètres définis dans `settings`.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.open(mySettings);
      ```

* **Close (winjs : close)**

   Effectue le suivi de fermeture d’un média pour l’élément média nommé *`name`*.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **Play (winjs : play)**

   Effectue le suivi de lecture d’un média pour l’élément média nommé *`name`* à un décalage *offset* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **Complete (winjs : complete)**

   Marque manuellement l’élément multimédia comme terminé au décalage *offset* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **Stop (winjs : stop)**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage *offset* donné.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **Cliquez sur (winjs : click)**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **Track (winjs : track)**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```js
      ADB.Media.track("mediaName",  null);
      ```

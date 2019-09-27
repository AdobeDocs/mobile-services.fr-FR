---
description: Informations sur la mesure des vidéos sur Android à l’aide de la solution de mesure vidéo.
keywords: android;library;mobile;sdk
seo-description: Informations sur la mesure des vidéos sur Android à l’aide de la solution de mesure vidéo.
seo-title: 'Chemin '
solution: Marketing Cloud,Analytics
title: 'Chemin '
topic: Développeur et mise en œuvre
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Chemin    {#video-analytics}

Informations sur la mesure des vidéos sur Android à l’aide de la solution de mesure vidéo.

>[!TIP]
>
>Au cours de la lecture vidéo, de fréquents appels de « pulsation » sont envoyés à ce service afin de mesurer la durée de lecture. Ces appels de pulsation sont envoyés toutes les dix secondes, ce qui se traduit par des mesures d’engagement vidéo granulaires et par des rapports d’abandons vidéo plus précis. For more information about Adobe's video measurement solution, see Measuring audio and video in Adobe Analytics.[](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

Le processus général de mesure vidéo se ressemble sur toutes les plateformes. Ce contenu présente un aperçu des tâches des développeurs avec des exemples de codes. Le tableau suivant répertorie les données multimédias envoyées à Analytics. Processing rules are used to map the context data to an Analytics variable.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Variable type: eVar
      * Délai d’expiration par défaut : Visite
      * Insight personnalisé (s.prop, utilisé pour le cheminement vidéo)
   * (**Obligatoire**) Lorsqu’un visiteur affiche une vidéo d’une certaine manière, cette variable de données contextuelles collecte le nom de la vidéo, tel que spécifié dans la mise en œuvre. Vous pouvez ajouter des classifications pour cette variable.
   * (**Facultatif**) La variable Insight personnalisé fournit des informations sur le cheminement vidéo.

* **a.media.name**
   * Type de variable : Custom Insight (s.prop)
   * **(Facultatif)** Fournit des informations de cheminement vidéo.

      >[!IMPORTANT]
      >
      >Le cheminement doit être activé par ExpCare pour cette variable.
   * Type d’événement : Insight personnalisé (s.prop)

* **a.media.segment**
   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue
   * (**Obligatoire**) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo.

      Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the Segments eVar: `1:M:0-25`.

      La méthode par défaut de collecte des données sur les vidéos collecte les données aux points suivants :

      * début de la vidéo (lecture)
      * début du segment
      * fin de la vidéo (arrêt)
      Analytics compte l’affichage du premier segment au début du segment, lorsque le visiteur commence la lecture. Les affichages de segments suivants commencent au démarrage du segment.


* **a.contentType**
   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue
   * Collecte les données sur le type de contenu affiché par un visiteur.

      Les envois d’accès par mesures vidéo se voient attribuer un type de contenu `video`. Du point de vue des mesures vidéo, le **type de contenu** permet d’identifier les visiteurs de vidéos et donc de calculer les taux de conversion vidéo.

* **a.media.timePlayed**
   * Type de variable : Evénement
   * Type : compteur
   * Compte le temps de lecture vidéo passé, en secondes, depuis le dernier processus de collecte de données (demande d’image).

* **a.media.view**
   * Type de variable : Evénement
   * Type : compteur
   * Indique qu’un visiteur a visionné une partie d’une vidéo.

      Cependant, cette variable ne fournit aucune information quant au pourcentage, ni à la portion de la vidéo que le visiteur a visionnée.

* **a.media.segmentView**
   * Variable type: Event
   * Type : compteur
   * Indique qu’un visiteur a visionné une partie d’un segment de vidéo.

      Cependant, cette variable ne fournit aucune information quant au pourcentage, ni à la portion de la vidéo que le visiteur a visionnée.

* **a .media.complete**
   * Type de variable : Evénement
   * Type : compteur
   * Indique qu’un utilisateur a visionné une vidéo dans son intégralité.

      Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et d’autres diffusions sans fin définie, vous pouvez indiquer un point personnalisé auquel la mesure se termine (par exemple, une durée spécifique visionnée).


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configurez un objet `MediaSettings` avec les paramètres que vous voulez utiliser pour effectuer le suivi de la vidéo :

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Par exemple, lorsque le lecteur est en pause, appelez `mediaStop`. `mediaPlay` est appelé lorsque la lecture démarre ou reprend.

## Classes {#section_16838332727348F990305C0C6B0D795C}

**Classe : MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Classe : MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

Voici les méthodes de la classe Media Measurement :

* **settingsWith**

   Renvoie un objet `MediaSettings` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Renvoie un objet `MediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.
   * Voici la syntaxe de cette méthode :

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Ouvre un objet `MediaSettings` pour le suivi.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Ferme l’élément multimédia nommé *name*.

      * Voici la syntaxe de cette méthode :
      ```java
      public static void close(String name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.close("name"); 
      ```


* **play**
   * Lit l’élément multimédia nommé *name* au décalage (*offset*) donné en secondes.
   * Voici la syntaxe de cette méthode :

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **terminé**

   Marque manuellement l’élément multimédia comme terminé au décalage (*offset*) donné en secondes.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void complete(String name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage *offset* donné.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void stop(String name, double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void click(String name double offset); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.click("name", 0);
      ```

* **track**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Media.track("name", null); 
      ```

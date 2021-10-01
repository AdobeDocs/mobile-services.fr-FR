---
description: Cette section contient des informations sur la mesure des vidéos sous iOS au moyen de la mesure Jalon.
solution: Experience Cloud,Analytics
title: Analyses de vidéos
topic-fix: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
exl-id: d4d11ca0-1280-49db-8983-5b6d83856482
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 94%

---

# Analyses de vidéos  {#video-analytics}

Cette section contient des informations sur la mesure des vidéos sous iOS au moyen de la mesure Jalon.

>[!TIP]
>
>Au cours de la lecture vidéo, de fréquents appels de « pulsation » sont envoyés à ce service afin de mesurer la durée de lecture. Ces appels de pulsation sont envoyés toutes les dix secondes, ce qui se traduit par des mesures d’engagement vidéo granulaires et par des rapports d’abandons vidéo plus précis. Pour plus d’informations, voir [Mesure des médias en flux continu dans Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=fr).

Le processus général de mesure vidéo est très similaire sur toutes les plateformes. Ce contenu présente un aperçu de base des tâches des développeurs avec des exemples de codes.

## Mise en correspondance des événements du lecteur avec les variables Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

Le tableau suivant répertorie les données multimédias envoyées à Analytics. Utilisez des règles de traitement pour mapper les données contextuelles à une variable Analytics.

* **a.media.name**

   (Obligatoire) Collecte le nom de la vidéo, tel que spécifié dans l’implémentation, lorsqu’un visiteur regarde la vidéo d’une manière ou d’une autre. Vous pouvez ajouter des classifications pour cette variable.

   (Facultatif) La variable Custom Insight fournit des informations de cheminement vidéo.

   * Type de variable : eVar
   * Délai d’expiration par défaut : Visite
   * Custom Insight (s.prop, utilisée pour le cheminement vidéo)

* **a.media.name**

   (Facultatif) Fournit des informations de cheminement vidéo. Pour cette variable, le cheminement doit être activé par l’assistance clientèle.

   * Type de variable : Insight personnalisé (s.prop)
   * Type d’événement : Insight personnalisé (s.prop)

* **a.media.segment**

   (Obligatoire) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo. Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur. Par exemple, lorsqu’un visiteur affiche le premier segment dans une vidéo, SiteCatalyst peut collecter les éléments suivants dans l’eVar de segments `1:M:0-25`.

   La méthode de collecte de données vidéo par défaut collecte les données aux points suivants :

   * lorsque la vidéo démarre (lecture) ;
   * lorsque le segment débute ;
   * lorsque la vidéo prend fin (arrêt).

   Analytics comptabilise la première vue du segment au début du segment, lorsque le visiteur commence à regarder. Les vues des segments suivants démarrent au début des segments.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue


* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les accès envoyés par mesure vidéo se voient attribuer un type de contenu de `video`. Cette variable ne doit pas être réservée exclusivement au suivi vidéo. Le fait d’obtenir un autre type de contenu de rapport de contenu en utilisant cette même variable vous permet d’analyser la distribution des visiteurs par rapport aux différents types de contenu. Par exemple, vous pouvez baliser d’autres types de contenu à l’aide de valeurs telles que &quot;article&quot; ou &quot;page de produit&quot; à l’aide de cette variable. Du point de vue des mesures vidéo, le type de contenu permet d’identifier les visiteurs de vidéos et de calculer les taux de conversion vidéo.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue

* **a.media.timePlayed**

   Compte le temps de lecture vidéo passé, en secondes, depuis le dernier processus de collecte de données (requêtes d’images).

   * Type de variable : Evénement
   * Type : compteur

* **a.media.view**

   Indique qu’un visiteur a visionné une partie d’une vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée, ni la partie visionnée.

   * Type de variable : Evénement
   * Type : compteur

* **a.media.segmentView**

   Indique qu’un visiteur a visionné une partie d’un segment de vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée, ni la partie visionnée.

   * Type de variable : Evénement
   * Type : compteur

* **a.media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et les autres flux qui n’ont pas de fin définie, vous pouvez spécifier un point personnalisé pour mesurer les vidéos terminées, par exemple, après un moment spécifique de visionnage.

   * Type de variable : Evénement
   * Type : compteur

## Configuration des paramètres multimédias {#section_929945D4183C428AAF3B983EFD3E2500}

Configurez un objet `ADBMediaSettings` avec les paramètres que vous souhaitez pour suivre les vidéos :

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Suivi des événements du lecteur {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Pour mesurer la lecture de vidéos, appelez les méthodes `mediaPlay`, `mediaStop`, et `mediaClose` aux moments opportuns. Par exemple, lorsque le lecteur est en pause : `mediaStop`. `mediaPlay` est appelé lorsque la lecture démarre ou reprend.

L’exemple suivant montre comment configurer des notifications et appeler des méthodes multimédias pour mesurer les vidéos :

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Classes {#section_16838332727348F990305C0C6B0D795C}

### Classe : ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Classe : ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Références pour les méthodes et classes de mesure d’éléments multimédias {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   Renvoie un objet `ADBMediaSettings` avec les paramètres spécifiés.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   Renvoie un objet `ADBMediaSettings` à utiliser pour le suivi d’une vidéo publicitaire.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   Ouvre un objet `ADBMediaSettings` pour le suivi.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Ferme l’élément multimédia nommé *name*.

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Lit le *nom* nommé de l’élément multimédia au *décalage* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Marque manuellement l’élément multimédia comme terminé au décalage *offset* donné (en secondes).

   * Voici la syntaxe de cette méthode :

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage *offset* donné.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Voici l’exemple de code pour cette méthode :

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```

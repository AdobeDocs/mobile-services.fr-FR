---
description: Cette section contient des informations sur la mesure des vidéos sous iOS au moyen de la mesure Jalon.
seo-description: Cette section contient des informations sur la mesure des vidéos sous iOS au moyen de la mesure Jalon.
seo-title: 'Chemin '
solution: Marketing Cloud,Analytics
title: 'Chemin '
topic: Développeur et mise en œuvre
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Chemin    {#video-analytics}

Cette section contient des informations sur la mesure des vidéos sous iOS au moyen de la mesure Jalon.

>[!TIP]
>
>Au cours de la lecture vidéo, de fréquents appels de « pulsation » sont envoyés à ce service afin de mesurer la durée de lecture. Ces appels de pulsation sont envoyés toutes les dix secondes, ce qui se traduit par des mesures d’engagement vidéo granulaires et par des rapports d’abandons vidéo plus précis. Pour plus d’informations, voir [Mesure des données audio et vidéo dans Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html).

Le processus général de mesure vidéo se ressemble sur toutes les plateformes. Cette section donne une vue d’ensemble des tâches du développeur et fournit des exemples de code.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

Le tableau suivant répertorie les données multimédias envoyées à Analytics. Utilisez des règles de traitement pour mapper les données contextuelles à une variable Analytics.

* **a.media.name**

   (Obligatoire) Collecte le nom de la vidéo, comme spécifié dans la mise en œuvre, lorsqu’un visiteur affiche une vidéo d’une certaine manière. Vous pouvez ajouter des classifications pour cette variable.

   (Facultatif) La variable Insight personnalisé fournit des informations sur le cheminement vidéo.

   * Type de variable : eVar
   * Délai d’expiration par défaut : Visite
   * Insight personnalisé (s.prop, utilisé pour le cheminement vidéo)

* **a.media.name**

   (Facultatif) Fournit des informations de cheminement vidéo. Le cheminement doit être activé par le service à la clientèle pour cette variable.

   * Type de variable : Custom Insight (s.prop)
   * Type d’événement : Insight personnalisé (s.prop)

* **a.media.segment**

   (Obligatoire) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo. Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` Segments evar.

   La méthode par défaut de collecte des données sur les vidéos collecte les données aux points suivants :

   * début de la vidéo (lecture)
   * début du segment
   * fin de la vidéo (arrêt)
   Analytics compte l’affichage du premier segment au début du segment, lorsque le visiteur commence la lecture. Les affichages de segments suivants commencent au démarrage du segment.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue


* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les envois d’accès par mesures vidéo se voient attribuer un type de contenu `video`. Cette variable ne doit pas être exclusivement réservée au suivi vidéo. Les autres types de contenu des rapports de contenu utilisant la même variable vous permettent d’analyser la distribution des visiteurs par rapport aux différents types de contenu. Par exemple, vous pouvez baliser les types de contenu en utilisant des valeurs telles que « article » ou « page de produits » à l’aide de cette variable. Du point de vue des mesures vidéo, le type de contenu permet d’identifier les visiteurs de vidéos et de calculer les taux de conversion vidéo.

   * Type de variable : eVar
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

* **a.media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et d’autres diffusions sans fin définie, vous pouvez indiquer un point personnalisé auquel la mesure se termine, par exemple, une durée spécifique visionnée.

   * Type de variable : Evénement
   * Type : compteur

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

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

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Par exemple, lorsque le lecteur est en pause : `mediaStop`. `mediaPlay` est appelé lorsque la lecture démarre ou reprend.

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

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

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


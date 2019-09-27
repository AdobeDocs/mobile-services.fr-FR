---
description: Le processus général de mesure vidéo se ressemble dans toutes les plates-formes AppMeasurement. This section provides a basic overview of the developer tasks along with code samples.
seo-description: Le processus général de mesure vidéo se ressemble dans toutes les plates-formes AppMeasurement. Cette section présente un aperçu de base des tâches du développeur, ainsi que des exemples de code.
seo-title: 'Chemin '
title: 'Chemin '
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Chemin    {#video-analytics}

Le processus général de mesure vidéo se ressemble dans toutes les plates-formes AppMeasurement. This section provides a basic overview of the developer tasks along with code samples.

Pour plus d’informations sur les mesures vidéo, voir la section [Mesure audio et vidéo dans le guide Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) .  Le tableau ci-après répertorie les données multimédias envoyées à Analytics. Utilisez des règles de traitement pour mapper les données contextuelles de la colonne Variable de données contextuelles avec les variables Analytics de la colonne Type de variable.

## Association des événements du lecteur aux variables Analytics

* **a.media.name**

   (Requis) Collecte le nom de la vidéo, comme spécifié lors de la mise en œuvre, lorsqu’un visiteur visionne la vidéo de quelque manière que ce soit. Vous pouvez ajouter des classifications pour cette variable.

   **(Optional)** The Custom Insight variable provides video pathing information.

   * Nom de variable : eVar
      * Délai d’expiration par défaut : Visite
      * Insight personnalisé (s.prop, utilisé pour le cheminement vidéo)

* **a.media.name**

   (**Facultatif)** Fournit des informations de cheminement vidéo. Le cheminement doit être activé par le service à la clientèle pour cette variable.

   * Type d’événement : Insight personnalisé (s.prop)
   * Insight personnalisé (s.prop)

* **a.media.segment**

   (**Obligatoire**) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo. Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. The default video data collection method collects data at the video start (play), segment begin, and video end (stop) points.

   Analytics compte l’affichage du premier segment au début du segment, lorsque le visiteur commence la lecture. Les affichages de segments suivants commencent au démarrage du segment.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue

* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les envois d’accès par mesure vidéo se voient attribuer un type de contenu « vidéo ». Cette variable ne doit pas être exclusivement réservée au suivi vidéo. Les autres types de contenu des rapports de contenu utilisant la même variable permettent d’analyser la distribution des visiteurs par rapport aux différents types de contenu. Par exemple, vous pouvez baliser les types de contenu en utilisant des valeurs telles que « article » ou « page de produits » à l’aide de cette variable. Du point de vue des mesures vidéo, le type de contenu permet d’identifier les visiteurs de vidéos et donc de calculer les taux de conversion vidéo.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue

* **a.media.timePlayed**

   Compte le temps de lecture vidéo passé, en secondes, depuis le dernier processus de collecte de données (requêtes d’images).

   * Variable type: Event
   * Type : compteur

* **a.media.view**

   Indique qu’un visiteur a visionné une partie d’une vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardé (ni la partie visionnée).

   * Variable type: Event
   * Type : compteur

* **a.media.segmentView**

   Indique qu’un visiteur a visionné une partie d’un segment de vidéo. Cependant, cette mesure ne fournit aucune information quant au pourcentage de la vidéo que le visiteur a regardée (ni la partie visionnée).

   * Variable type: Event
   * Type : compteur

* **a .media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et les autres flux qui n’ont pas de fin définie, vous pouvez spécifier un point personnalisé pour mesurer la fin. Par exemple, après un temps de lecture spécifique.

   * Type de variable : Evénement
   * Type : compteur

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Par exemple, lorsque le lecteur est en pause : `mediaStop`. `mediaPlay` est appelé lorsque la lecture démarre ou reprend.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Ouvre une vidéo pour suivi.

   * Voici la syntaxe de cette méthode :

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Ouvre un objet `MediaSettings` pour le suivi.

   * Voici la syntaxe de cette méthode :

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Ferme l’élément multimédia nommé *`name`*.

   * Voici la syntaxe de cette méthode :

      ```cpp
      void close(QString name);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * Voici la syntaxe de cette méthode :

      ```cpp
      void play(QString name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **terminé**

   Marque manuellement l’élément multimédia comme terminé au décalage *`offset`donné (en secondes).*

   * Voici la syntaxe de cette méthode :

      ```cpp
      void complete(QString name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Avertit le module multimédia que la vidéo a été interrompue ou suspendue au décalage *offset* donné.

   * Voici la syntaxe de cette méthode :

      ```cpp
      stop(QString name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Avertit le module multimédia qu’un utilisateur a cliqué sur l’élément multimédia.

   * Voici la syntaxe de cette méthode :

      ```cpp
      void click(QString name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Envoie un appel d’action de suivi (aucune page vue) pour l’état multimédia en cours.

   * Voici la syntaxe de cette méthode :

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```

---
description: Le processus général de mesure vidéo est très similaire sur toutes les plateformes AppMeasurement. Cette section présente un aperçu de base des tâches des développeurs ainsi que des exemples de code.
title: Analyses de vidéos
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
exl-id: 90da1a9e-2faa-429c-969e-869ebedf08cc
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 69%

---

# Analyses de vidéos  {#video-analytics}

Le processus général de mesure vidéo est très similaire sur toutes les plateformes AppMeasurement. Cette section présente un aperçu de base des tâches des développeurs ainsi que des exemples de code.

Pour plus d’informations sur les mesures vidéo, consultez le guide [Mesure des médias en flux continu dans Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=fr) .  Le tableau suivant répertorie les données multimédias envoyées à Analytics. Utilisez des règles de traitement pour mapper les données contextuelles de la colonne Variable de données contextuelles à une variable Analytics, comme décrit dans la colonne Type de variable .

## Mise en correspondance des événements du lecteur avec les variables Analytics

* **a.media.name**

   (Obligatoire) Collecte le nom de la vidéo, tel que spécifié dans la mise en oeuvre, lorsqu’un visiteur regarde la vidéo d’une manière ou d’une autre. Vous pouvez ajouter des classifications pour cette variable.

   **(Facultatif)** La variable Custom Insight fournit des informations de cheminement vidéo.

   * Nom de variable : eVar
      * Délai d’expiration par défaut : Visite
      * Custom Insight (s.prop, utilisée pour le cheminement vidéo)

* **a.media.name**

   (**Facultatif)** Fournit des informations de cheminement vidéo. Pour cette variable, le cheminement doit être activé par l’assistance clientèle.

   * Type d’événement : Insight personnalisé (s.prop)
   * Custom Insight (s.prop)

* **a.media.segment**

   (**Obligatoire**) Collecte des données de segments de vidéos, notamment le nom du segment et l’ordre d’apparition du segment dans la vidéo. Cette variable est renseignée en activant la variable `segmentByMilestones` lors du suivi automatique des événements du lecteur ou en configurant un nom de segment personnalisé lors du suivi manuel des événements du lecteur.

   Par exemple, lorsqu’un visiteur affiche le premier segment dans une vidéo, SiteCatalyst peut collecter `1:M:0-25` dans l’eVar Segments. La méthode de collecte de données vidéo par défaut collecte des données au démarrage (lecture) de la vidéo, au début du segment et à la fin de la vidéo (arrêt).

   Analytics comptabilise la première vue du segment au début du segment, lorsque le visiteur commence à regarder. Les vues des segments suivants démarrent au début des segments.

   * Type de variable : eVar
   * Délai d’expiration par défaut : page vue

* **a.contentType**

   Collecte les données sur le type de contenu affiché par un visiteur. Les accès envoyés par mesure vidéo se voient attribuer un type de contenu &quot;vidéo&quot;. Cette variable ne doit pas être réservée exclusivement au suivi vidéo. L’utilisation d’un autre type de contenu de rapport de contenu à l’aide de cette même variable vous permet d’analyser la répartition des visiteurs entre les différents types de contenu. Par exemple, vous pouvez baliser d’autres types de contenu à l’aide de valeurs telles que &quot;article&quot; ou &quot;page de produit&quot; à l’aide de cette variable. Du point de vue des mesures vidéo, le type de contenu permet d’identifier les visiteurs de vidéos et donc de calculer les taux de conversion vidéo.

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

* **a .media.complete**

   Indique qu’un utilisateur a visionné une vidéo dans son intégralité. Par défaut, la fin de l’événement est mesurée 1 seconde avant la fin de la vidéo. Pendant la mise en œuvre, vous pouvez spécifier combien de secondes à partir de la fin de la vidéo vous souhaitez considérer comme une lecture intégrale. Pour les vidéos en direct et les autres flux qui n’ont pas de fin définie, vous pouvez spécifier un point personnalisé pour mesurer la fin. Par exemple, après un temps de lecture spécifique.

   * Type de variable : Evénement
   * Type : compteur

## Suivi des événements du lecteur {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Pour mesurer la lecture de vidéos, appelez les méthodes `mediaPlay`, `mediaStop`, et `mediaClose` aux moments opportuns. Par exemple, lorsque le lecteur est en pause : `mediaStop`. `mediaPlay` est appelé lorsque la lecture démarre ou reprend.

## Références pour les méthodes et classes de mesure d’éléments multimédias {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Ouvre une vidéo pour le suivi.

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

   Lit l’élément multimédia nommé *`name`* à la valeur *`offset`* donnée (en secondes).

   * Voici la syntaxe de cette méthode :

      ```cpp
      void play(QString name, double offset);
      ```

   * Voici l’exemple de code pour cette méthode :

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **terminé**

   Marque manuellement l’élément multimédia comme terminé au décalage *`offset`* donné (en secondes).

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

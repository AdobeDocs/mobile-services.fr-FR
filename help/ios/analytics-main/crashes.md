---
description: Ces informations vous aident à comprendre le mode de suivi des blocages ainsi que les bonnes pratiques pour traiter les faux blocages.
seo-description: Ces informations vous aident à comprendre le mode de suivi des blocages ainsi que les bonnes pratiques pour traiter les faux blocages.
seo-title: Suivi des blocages d’application
solution: Experience Cloud,Analytics
title: Suivi des blocages d’application
topic: Développeur et mise en œuvre
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Suivi des blocages d’application{#track-app-crashes}

Ces informations vous aident à comprendre le mode de suivi des blocages ainsi que les bonnes pratiques pour traiter les faux blocages.

>[!IMPORTANT]
>
>Il est recommandé d’effectuer une mise à niveau vers la version 4.8.6 du SDK iOS : celle-ci contient d’importantes modifications qui empêchent le signalement de faux plantages.

## À quel moment Adobe signale-t-il un plantage ?

Lorsque votre application est arrêtée avant d’avoir été mise en arrière-plan, le SDK signale un plantage au prochain lancement de l’application.

## Comment le signalement de plantages fonctionne-t-il ?

iOS utilise des notifications système qui permettent aux développeurs de suivre et de gérer différents états et événements du cycle de vie de l’application.

Le SDK iOS Adobe Mobile est doté d’un gestionnaire de notifications répondant à la notification `UIApplicationDidEnterBackgroundNotification`. Dans ce code, une valeur est définie et indique que l’utilisateur a mis l’application en arrière-plan. Au prochain lancement, si cette valeur n’est pas trouvée, un plantage est signalé.

## Pourquoi Adobe mesure-t-il les plantages de cette façon ?

Cette approche consistant à mesurer les plantages permet de répondre efficacement à la question : *l’utilisateur a-t-il volontairement quitté mon application ?*

Les bibliothèques de rapport de plantages fournies par des sociétés comme Apteligent (anciennement appelée Crittercism) utilisent un gestionnaire `NSException` global pour offrir des rapports de plantages plus détaillés. Votre application ne peut pas utiliser plus d’un gestionnaire de ce type. Adobe a décidé de ne pas mettre en œuvre de gestionnaire `NSException` global afin d’éviter les erreurs de compilation, tout en sachant que ses clients peuvent utiliser d’autres fournisseurs de rapports de plantages.

## Qu’est-ce qui peut provoquer le signalement d’un faux blocage ?

Les scénarios suivants sont connus pour causer par erreur le signalement d’un plantage par le SDK :

* Si vous effectuez un débogage à l’aide de Xcode, un plantage peut survenir si vous lancez de nouveau l’application en avant-plan.

   >[!TIP]
   >
   >Dans ce scénario, vous pouvez éviter un plantage en mettant l’application en arrière-plan avant de la lancer de nouveau à partir de Xcode.

* Si votre application est en arrière-plan et envoie des accès Analytics par l’intermédiaire d’un appel qui n’est pas `trackActionFromBackground`, `trackLocation` ou `trackBeacon` et que celle-ci est arrêtée (manuellement ou par le système d’exploitation) alors qu’elle est en arrière-plan, un plantage survient lors du prochain lancement.

   >[!TIP]
   >
   >Une activité en arrière-plan dépassant le seuil du délai d’expiration du cycle de vie `lifecycleTimeout` peut également provoquer un faux lancement.

* Si votre application est lancée en arrière-plan (en raison d’une récupération en arrière-plan, d’une mise à jour d’emplacement, etc.) et qu’elle est arrêtée généralement par le système d’exploitation sans jamais s’afficher en avant-plan, un plantage survient au lancement suivant (à l’arrière-plan ou à l’avant-plan).
* Si vous supprimez l’indicateur de pause par programmation à partir de `NSUserDefaults` alors que l’application est en arrière-plan, un plantage survient lors du prochain lancement ou de la reprise.

## Comment peut-on éviter le signalement de faux plantages ?

Les procédures suivantes peuvent vous aider à empêcher que de faux plantages ne soient signalés :

* Dans la version 4.8.6 du SDK iOS, du code a été ajouté pour mieux déterminer si une nouvelle session de cycle de vie est réellement souhaitée.

   Ce code permet de corriger les faux plantages nº 2 et nº 3 de la section précédente.

* Veillez à procéder à votre développement avec des suites de rapports hors production, ce qui devrait empêcher que le plantage nº 1 ne survienne.
* Ne supprimez et ne modifiez aucune valeur placée dans `NSUserDefaults` par le SDK Adobe Mobile.

   Si ces valeurs sont modifiées en dehors du SDK, les données reportées seront invalides.


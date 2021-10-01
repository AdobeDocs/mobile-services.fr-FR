---
description: Si votre application permet d’ouvrir du contenu web mobile, vous devez vous assurer que les visiteurs ne sont pas ré-identifiés à chaque fois qu’ils passent de l’application native à l’application web mobile.
solution: Experience Cloud,Analytics
title: Suivi des visiteurs entre une application et le web mobile
topic-fix: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
exl-id: d8459d59-0edd-42c4-81b5-529b250accb4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 100%

---

# Suivi des visiteurs entre une application et le web mobile   {#visitor-tracking-between-an-app-and-mobile-web}

Si votre application permet d’ouvrir du contenu web mobile, vous devez vous assurer que les visiteurs ne sont pas ré-identifiés à chaque fois qu’ils passent de l’application native à l’application web mobile.

## Identifiants visiteurs dans les applications

Le SDK iOS génère un ID de visiteur unique lorsqu’une application est installée. Cet ID est stocké en mémoire persistante sur l’appareil mobile et est envoyé avec chaque accès. Il est supprimé uniquement lorsque l’utilisateur désinstalle l’application.

>[!TIP]
>
>Les ID visiteur de l’application sont conservés lors des mises à niveau.

## ID visiteur dans le web mobile

Les mises en œuvre type du web mobile utilisent le même `s_code.js` standard d’Analytics ou `AppMeasurement.js` que celui utilisé pour les environnements de bureau. Les bibliothèques JavaScript disposent de leurs propres méthodes de génération d’ID de visiteur uniques, ce qui engendre la création d’un ID de visiteur différent lorsque vous ouvrez le contenu web mobile depuis l’application.

Pour utiliser le même ID visiteur dans l’application et le web mobile, et transmettre l’ID visiteur de l’application au web mobile dans l’URL :

## Implémentation du suivi des visiteurs entre une application et le web mobile {#section_EDC91D6C67AD43999227707C2769C65D}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Afin d’ajouter des informations sur les visiteurs à l’URL utilisée pour ouvrir l’affichage web, appelez `visitorAppendToURL` :

   ```objective-c
   NSURL *url = [NSURL URLWithString:@"https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   À partir du SDK version 4.16.0, vous pouvez appeler `visitorGetUrlVariablesAsync:` et générer votre propre URL :

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

Le code du service d’ID sur le domaine de destination extrait le MID de l’URL au lieu d’envoyer une requête à Adobe pour le nouvel ID. Le code du service d’ID sur la page de destination utilise le MID transmis pour effectuer le suivi du visiteur.

Dès les premiers accès depuis le contenu web mobile, vérifiez que le paramètre `mid` est bien présent pour chaque accès et que sa valeur correspond à celle du `mid` envoyé par le code de l’application.

## Dépannage du suivi des visiteurs {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### Je ne vois pas `[ADBMobile visitorAppendToURL:]`.

Vérifiez que la version du SDK Adobe groupé dans l’application parente est 4.12.0 ou supérieure.

### Je ne vois pas les identifiants Adobe ID dans mon URL.

Vérifiez les éléments suivants :

* La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par `[ADBMobile visitorAppendToURL:]`

* Les identifiants Adobe ID sont encodés.

   Pour vérifier que les identifiants ont été ajoutés à l’URL ouverte, recherchez le paramètre de requête `adobe_mc`.

### Mon « mid » n’est pas le même dans l’application et dans l’affichage web.*

Vérifiez les éléments suivants :

* La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par `[ADBMobile visitorAppendToURL:]`

   La chaîne d’URL contient les paramètres Adobe.

   La chaîne doit contenir `adobe_mc="SAMPLE_ID_DATA"`, où `"SAMPLE_ID_DATA"` contient les ID générés dans le SDK Adobe Mobile.

* La version de `VisitorAPI.js` doit être 1.7.0 ou supérieure.

Si les problèmes persistent, contactez le service à la clientèle Adobe. Vous devrez être en mesure de partager votre application et le site associé pour qu’Adobe puisse valider la mise en œuvre.

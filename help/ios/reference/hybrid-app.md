---
description: Si votre application permet d’ouvrir du contenu web mobile, vous devez vous assurer que les visiteurs ne sont pas ré-identifiés à chaque fois qu’ils passent de l’application native à l’application web mobile.
seo-description: Si votre application permet d’ouvrir du contenu web mobile, vous devez vous assurer que les visiteurs ne sont pas ré-identifiés à chaque fois qu’ils passent de l’application native à l’application web mobile.
seo-title: Suivi des visiteurs entre une application et le web mobile
solution: Marketing Cloud,Analytics
title: Suivi des visiteurs entre une application et le web mobile
topic: Développeur et mise en œuvre
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Visitor tracking between an app and mobile web  {#visitor-tracking-between-an-app-and-mobile-web}

Si votre application permet d’ouvrir du contenu web mobile, vous devez vous assurer que les visiteurs ne sont pas ré-identifiés à chaque fois qu’ils passent de l’application native à l’application web mobile.

## Identifiants visiteur dans les applications

Le SDK iOS génère un identifiant visiteur unique à l’installation de l’application. Cet identifiant est stocké dans une mémoire persistante sur l’appareil mobile et envoyé avec chaque accès. Il est supprimé uniquement lorsque l’utilisateur désinstalle l’application..

>[!TIP]
>
>Les identifiants des visiteurs de l’application persistent grâce aux mises à niveau.

## Identifiants des visiteurs sur le Web mobile

Les mises en œuvre type du web mobile utilisent le même `s_code.js` standard d’Analytics ou `AppMeasurement.js` que celui utilisé pour les environnements de bureau. Les bibliothèques JavaScript disposent de leurs propres méthodes de génération d’ID visiteur uniques, ce qui engendre la création d’un ID visiteur différent lorsque vous ouvrez le contenu web mobile depuis l’application.

Pour utiliser le même identifiant visiteur dans l’application et le Web mobile et transmettre l’identifiant visiteur de l’application au Web mobile dans l’URL :

## Implement visitor tracking between an app and mobile web {#section_EDC91D6C67AD43999227707C2769C65D}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans Mise en oeuvre [principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Afin d’ajouter des informations sur les visiteurs à l’URL utilisée pour ouvrir l’affichage web, appelez `visitorAppendToURL` :

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
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

Le code du service d’ID sur le domaine de destination extrait le MID de l’URL au lieu d’envoyer une requête à Adobe pour demander un nouvel identifiant. Le code du service d’ID sur la page de destination utilise le MID transmis pour suivre le visiteur.

Dès les premiers accès depuis le contenu web mobile, vérifiez que le paramètre `mid` est bien présent pour chaque accès et que sa valeur correspond à celle du `mid` envoyé par le code de l’application.

## Résolution des problèmes de suivi des visiteurs {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### I do not see `[ADBMobile visitorAppendToURL:]`.

Vérifiez que la version du SDK Adobe groupé dans l’application parente est 4.12.0 ou supérieure.

### Je ne vois pas les identifiants Adobe ID dans mon URL.

Vérifiez les éléments suivants :

* La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par  `[ADBMobile visitorAppendToURL:]`

* Les identifiants Adobe ID sont encodés.

   To verify that IDs are appended to the URL that is being opened, look for the `adobe_mc` query parameter.

### Mon « mid » n’est pas le même dans l’application et dans l’affichage web.*

Vérifiez les éléments suivants :

* La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par `[ADBMobile visitorAppendToURL:]`

   La chaîne d’URL contient les paramètres Adobe.

   The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.

* La version de `VisitorAPI.js` doit être 1.7.0 ou supérieure.

Si les problèmes persistent, contactez le service à la clientèle Adobe. Vous devrez être en mesure de partager votre application et le site associé pour qu’Adobe puisse valider la mise en œuvre.

---
description: Si l’application ouvre un contenu de web mobile, assurez-vous que les visiteurs ne sont pas identifiés séparément lorsqu’ils se déplacent entre le web natif et le web mobile.
seo-description: Si l’application ouvre un contenu de web mobile, assurez-vous que les visiteurs ne sont pas identifiés séparément lorsqu’ils se déplacent entre le web natif et le web mobile.
seo-title: Suivi des visiteurs entre une application et le Web mobile
solution: Marketing Cloud,Analytics
title: Suivi des visiteurs entre une application et le Web mobile
topic: Développeur et mise en œuvre
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

Si l’application ouvre un contenu de web mobile, assurez-vous que les visiteurs ne sont pas identifiés séparément lorsqu’ils se déplacent entre le web natif et le web mobile.

## Identifiants visiteur dans les applications

Le SDK Android génère un ID visiteur unique lorsqu’une application est installée. Cet ID est stocké dans la mémoire persistante de l’appareil mobile, envoyé avec chaque accès et supprimé uniquement lorsque l’utilisateur désinstalle l’application.

>[!TIP]
>
>Les identifiants des visiteurs de l’application persistent grâce aux mises à niveau.

## Identifiants des visiteurs sur le Web mobile

Les mises en œuvre type du web mobile utilisent le même `s_code.js` standard d’Analytics ou `AppMeasurement.js` que celui utilisé pour les environnements de bureau. Les bibliothèques JavaScript disposent de leurs propres méthodes de génération d’ID visiteur uniques, ce qui engendre la création d’un ID visiteur différent lorsque vous ouvrez le contenu web mobile depuis l’application.

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

Pour utiliser le même identifiant visiteur pour l’application et le Web mobile :

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* IntelliJ IDEA ou Eclipse dans l’implémentation et le cycle de vie [](/help/android/getting-started/dev-qs.md)principaux.

1. Afin d’ajouter des informations sur les visiteurs à l’URL utilisée pour ouvrir l’affichage web, appelez `visitorAppendToURL` :

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   À partir du SDK version 4.16.0, vous pouvez appeler `Visitor.getUrlVariablesAsync` et générer votre propre URL :

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

Le code du service d’ID sur le domaine de destination extrait le MID de l’URL au lieu d’envoyer une requête de nouvel identifiant à Adobe. Le code utilise le MID transmis pour effectuer le suivi du visiteur.

Pour les accès depuis le contenu web mobile, vérifiez que le paramètre `mid` existe pour chaque accès et que cette valeur correspond au paramètre `mid` envoyé par le code de l’application.

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

Vérifiez que la version du SDK Adobe groupé dans l’application parente est 4.12.0 ou supérieure.

**Je ne vois pas les identifiants Adobe ID dans mon URL.**

* Vérifiez les éléments suivants :
   * La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par `Visitor.appendToURL(urlString)`.
   * Les identifiants Adobe ID sont encodés.
To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### Mon `mid` est différent dans mon application et mon affichage web.

* Vérifiez les éléments suivants :

   * La chaîne d’URL utilisée pour ouvrir l’affichage web a été générée par `Visitor.appendToURL(urlString)`.
   * La chaîne d’URL contient les paramètres Adobe.

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * La version de `VisitorAPI.js` doit être 1.7.0 ou supérieure.

Si ces procédures de dépannage ne résolvent pas vos problèmes, contactez le service à la clientèle Adobe.

>[!IMPORTANT]
>
>Pour permettre à Adobe de valider l’implémentation, vous devez partager un exemple d’application et le site associé.


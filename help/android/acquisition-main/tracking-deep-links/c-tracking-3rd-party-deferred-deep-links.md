---
description: Utilisez le SDK Android pour mettre en œuvre le suivi de liens profonds différés tiers.
title: Suivi de liens profonds différés tiers
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
exl-id: d8cbc679-a512-44db-8c30-6a029ff738ae
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 84%

---

# Suivi de liens profonds différés tiers{#tracking-third-party-deferred-deep-links}

Utilisez le SDK Android pour mettre en œuvre le suivi de liens profonds différés tiers.

## Création de liens profonds classiques pour le SDK Adobe Mobile {#section_D114FA1EB9664EAA82E036A990694B26}

Le SDK Adobe Mobile prend actuellement en charge la création de liens profonds pour laquelle le développeur d’applications doit utiliser l’API SDK `collectLifecycleData` depuis l’activité de liens profonds. Le SDK ajoute les données de liens profonds depuis les paramètres d’URL de lien profond. Pour plus d’informations sur le fonctionnement des liens profonds dans le SDK Adobe Mobile, voir [Suivi des liens profonds](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Création de liens profonds Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Un créateur de publicités peut créer une publicité sur Facebook sous la forme d’un lien profond. Lorsque les utilisateurs cliquent sur la publicité, ils accèdent directement aux informations qui les intéressent dans l’application. Le lien profond **n’est pas** une URL d’empreinte digitale. Néanmoins, lors de la configuration de la publicité, il existe une option permettant de fournir une URL de lien profond tiers. Un développeur d’applications qui utilise les SDK et services Adobe Mobile doit saisir l’URL d’empreinte digitale configurée pour Adobe Mobile Service dans ce champ. Si tout est correctement configuré, le SDK Facebook transmet cette URL à l’application lorsque cette dernière est installée ou lancée.

## Configuration des SDK {#section_834CD3109175432B8173ECB6EA7DE315}

Pour se préparer à ajouter la prise en charge des liens profonds Facebook à l’aide du SDK Adobe Mobile, le développeur d’applications doit effectuer les tâches suivantes :

* Prise en main du SDK Android

   Pour plus d’informations, voir [Prise en main du SDK Android](https://developers.facebook.com/docs/android/getting-started).

* Configuration de liens profonds

   Pour plus d’informations, reportez-vous à la section [Configuration de liens profonds](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Si l’application est configurée correctement, l’API du `trackAdobeDeepLink()` doit activer la collecte des informations de liens profonds provenant de la campagne d’acquisition Facebook, puis les envoyer à Adobe Mobile Service. Si l’accès à l’installation n’a pas été envoyé à Adobe Mobile Service au premier lancement, ces informations seront ajoutées à l’accès du cycle de vie. Sinon, elle sera envoyée sous la forme d’un accès à un lien profond Adobe.

>[!TIP]
>
>Assurez-vous que l’URL de lien profond comporte une clé dénommée `a.deeplink.id`. Si le paramètre ID de lien profond est absent de l’URL, les paramètres d’URL ne sont pas ajoutés aux données contextuelles.

Si le lien peut être attribué à une acquisition, le SDK Adobe Mobile stocke les données d’acquisition provenant du lien profond Facebook qui a été utilisé pour appeler `trackAdobeDeepLink()`. Ces données seront disponibles pour le SDK Mobile Adobe lors des lancements ultérieurs. Si un rappel a été enregistré, le rappel d’Adobe est également utilisé pour renvoyer les données au client.

## Activation des liens profonds dans une application Android {#section_64C15E269E89424B8E3D029F88094620}

1. Enregistrez l’application pour traiter les liens profonds.

   Pour obtenir plus d’informations, voir [Autoriser d’autres applications à démarrer votre activité](https://developer.android.com/training/basics/intents/filters.html).

1. Liez les SDK Facebook.

   Pour ajouter la dépendance gradle Facebook à l’application, exécutez les étapes du document [Démarrer avec le SDK Android](https://developers.facebook.com/docs/android/getting-started).

1. Pour initialiser le SDK Facebook, suivez les instructions de la section *Configuration d’Android Studio*.
1. Appelez `trackAdobeDeepLink()` depuis l’activité principale.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

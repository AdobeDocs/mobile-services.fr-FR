---
product: services mobiles
audience: end-user
user-guide-title: Mobile Services Android Help
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Aide sur Mobile Services Android{#android}

+ [SDK Android 4.x pour solutions Experience Cloud](overview.md)
+ [Notes de mise à jour](rel-notes.md)
+ Prise en main{#getting-started-android}
   + [Prise en main](getting-started/getting-started.md)
   + [Before you start](getting-started/requirements.md)
   + [Core implementation and lifecycle](getting-started/dev-qs.md)
   + [Processing rules and context data](getting-started/proc-rules.md)
   + [Migration vers la bibliothèque Android 4.x](getting-started/migration-v3.md)
+ Configuration{#configuration-android}
   + [Présentation de la configuration](configuration/configuration.md)
   + [ADBMobile JSON config file](configuration/json-config/json-config.md)
   + [Override the ADBMobile JSON config path](configuration/json-config/json-config-remote.md)
   + [Traitement par lot des accès](configuration/hit-batching.md)
   + [Méthodes de configuration](configuration/methods.md)
+ [Mesures de cycle de vie](metrics.md)
+ Analytics{#analytics-android}
   + [Présentation d’Analytics](analytics-main/analytics-main.md)
   + [Suivi des états d’application](analytics-main/states.md)
   + [Suivi des actions d’application](analytics-main/actions.md)
   + [Suivi des blocages d’application](analytics-main/crashes.md)
   + [Actions minutées](analytics-main/timed-actions.md)
   + [Valeur de durée de vie du visiteur](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [Variable Produits](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [Sérialisation d’événements](analytics-main/event-serialization.md)
   + [Chemin ](analytics-main/video-qs.md)
   + Postbacks{#postbacks}
      + [Présentation des postbacks](analytics-main/postbacks/postbacks.md)
      + [Exemple de postbacks](analytics-main/postbacks/postback-example.md)
      + [Postbacks de type PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Méthodes Analytics](analytics-main/analytics-methods.md)
+ Acquisition{#acquisition-android}
   + [Présentation de l’acquisition](acquisition-main/acquisition-main-android.md)
   + [Acquisition d’applications mobiles](acquisition-main/acquisition.md)
   + [Méthodes d’acquisition](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Suivi des liens profonds différés tiers](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Test de l’acquisition de liens marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Test de l’acquisition V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Test de l’acquisition héritée](acquisition-main/t-testing-acquisition.md)
   + [Résolution des problèmes liés aux tests d’acquisition](acquisition-main/troubleshoot-acquisition-testing.md)
+ Messagerie{#messaging-android}
   + [Présentation de la messagerie](messaging-main/messaging-main-android.md)
   + In-app messaging{#inapp-messaging}
      + [In-app messaging](messaging-main/messaging/messaging.md)
      + [Résolution des problèmes de messagerie in-app](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [Messagerie push](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receive rich push notifications](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Résolution des problèmes de messagerie push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Emplacement{#location}
   + [Présentation de l'emplacement](location/location.md)
   + [Géolocalisation et points ciblés](location/geo-poi.md)
   + [Suivi des balises](location/beacon.md)
+ Target{#target-android}
   + [Présentation de Target](target-main/target-main.md)
   + [Configuration de Target](target-main/target.md)
   + [Méthodes Target](target-main/c-target-methods.md)
   + [Prérécupération du contenu des offres dans Android](target-main/c-mob-target-prefetch-android.md)
   + [Target Preview sous Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Présentation d’Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Configuration de l’ID Experience Cloud](c-marketing-cloud/mcvid.md)
   + [Méthodes d’Adobe Experience Platform Identity Service](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Présentation d’Audience Manager](audience-manager/audience-manager.md)
   + [Configuration d’Audience Manager](audience-manager/audiencemgmt.md)
   + [Méthodes d’Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearables{#wearables-android}
   + [Présentation du module Wearables](wearables/wearables.md)
   + [Android Wearables : démarrage](wearables/android-wearable.md)
   + [Android Wearables : notes supplémentaires](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Présentation du kit SDK Android](/help/android/reference/reference.md)
   + [ID d’application](/help/android/reference/app-ids.md)
   + [Visitor tracking between an app and mobile web](/help/android/reference/hybrid-app.md)
   + [Widgets Android](/help/android/reference/widgets.md)
+ Confidentialité et Règlement général sur la protection des données{#gdpr-privacy-android}
   + [Présentation de la confidentialité et du RMPC](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Récupération des identifiants stockés](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Définition de l’état d’acceptation de l’utilisateur](c-mob-privacy-gdpr-android/privacy.md)
+ Module externe PhoneGap{#phonegap-android}
   + [Présentation du module PhoneGap](phonegap/phonegap.md)
   + [PhoneGap plug-in methods](phonegap/phonegap-methods.md)

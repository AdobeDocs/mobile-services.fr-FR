---
product: mobile-services
audience: end-user
user-guide-title: Aide sur Mobile Services ios
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Aide sur Mobile Services ios {#ios}

+ [SDK iOS 4.x pour solutions Experience Cloud](overview.md)
+ [Notes de mise à jour](rel-notes.md)
+ Prise en main {#getting-started-ios}
   + [Présentation de prise en main](getting-started/getting-started.md)
   + [Avant de commencer](getting-started/requirements.md)
   + [Implémentation et cycle de vie principaux](getting-started/dev-qs.md)
   + [Règles de traitement et données contextuelles](getting-started/proc-rules.md)
   + [Intégration rapide](getting-started/swift-integration.md)
   + [Migration vers la bibliothèque ios 4. x](getting-started/migration-v3.md)
+ Configuration {#config-ios}
   + [Présentation de la configuration](configuration/configuration.md)
   + [Config JSON adbmobile](configuration/json-config/json-config.md)
   + [Remplacer le chemin de configuration JSON adbmobile](configuration/json-config/json-config-remote.md)
   + [Traitement par lot des accès](configuration/hit-batching.md)
   + [Méthodes de configuration](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Mesures de cycle de vie](metrics.md)
+ Analytics {#analytics-ios}
   + [Présentation d'Analytics](analytics-main/analytics-main.md)
   + [Suivi des états d’application](analytics-main/states.md)
   + [Suivi des actions d’application](analytics-main/actions.md)
   + [Suivi des blocages d'application](analytics-main/crashes.md)
   + [Actions minutées](analytics-main/timed-actions.md)
   + [Valeur de durée de vie du visiteur](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Variable products](analytics-main/products/products.md)
      + [Variable products avec evars de marchandisage et événements spécifiques aux produits](analytics-main/products/products-variable-evars-events.md)
   + [Sérialisation d’événements](analytics-main/event-serialization.md)
   + [Chemin ](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Présentation des postbacks](analytics-main/postback/postback.md)
      + [Exemple postback](analytics-main/postback/postback-example.md)
      + [Postbacks PII](analytics-main/postback/c-pii-postbacks.md)
   + [Méthodes Analytics](analytics-main/analytics-methods.md)
+ Acquisition {#acquisition-ios}
   + [Présentation de l'acquisition](acquisition-main/acquisition-main.md)
   + [Acquisition d'applications mobiles](acquisition-main/acquisition.md)
   + [Méthodes d'acquisition](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Suivi des liens profonds](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Suivi des liens profonds différés tiers](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Test de l'acquisition des liens marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Test V 3 acquisition](acquisition-main/t-testing-version-3-acquisition.md)
   + [Test de l'acquisition héritée](acquisition-main/t-testing-acquisition.md)
   + [Publicités Search Ads d’Apple](acquisition-main/c-apple-search-ads.md)
+ Messagerie {#messaging-ios}
   + [Présentation de la messagerie](messaging-main/messaging-main.md)
   + In-app messaging {#in-app-messaging}
      + [Messagerie in-app](messaging-main/messaging/messaging.md)
      + [Dépannage des messages in-app](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Messagerie Push](messaging-main/push-messaging/push-messaging.md)
      + [Mise en œuvre de messages Push avec liens profonds](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Recevoir des notifications Push riches](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Résolution des problèmes de messagerie Push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Emplacement {#location-ios}
   + [Présentation de l'emplacement](location/location.md)
   + [Géolocalisation et points ciblés](location/geo-poi.md)
   + [Suivi iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Présentation de Target](target-main/target-main.md)
   + [Méthodes Target](target-main/c-target-methods.md)
   + [Prérécupération du contenu des offres dans iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Target Preview sous iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Présentation de Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Méthodes du service d'identité Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Méthodes Audience Manager](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Implémentation Apple TV avec tvos](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target pour TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Méthodes TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [Implémentation d'extension ios](ios-ext/ios-ext.md)
   + [Implémentation d'extension autonome](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implémentation Apple Watch avec watchos 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [Référence du SDK ios](reference/reference.md)
   + [ID d’application](reference/app-ids.md)
   + [Suivi des visiteurs entre une application et un Web mobile](reference/hybrid-app.md)
   + [Versions des appareils ios](reference/device-versions.md)
+ Confidentialité et Règlement général sur la protection des données{#privacy-gdpr-ios}
   + [Confidentialité et Règlement général sur la protection des données](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Récupération des identifiants stockés](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Définition de l'état d'acceptation de l'utilisateur](c-mob-privacy-gdpr-ios/privacy.md)
+ Module externe PhoneGap {#phonegap-ios}
   + [Module phonegap](phonegap/phonegap.md)
   + [Méthodes du module phonegap](phonegap/phonegap-methods.md)

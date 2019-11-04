---
product: mobile-services
audience: end-user
user-guide-title: Aide sur Mobile Services iOS
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Aide sur Mobile Services iOS{#ios}

+ [SDK iOS 4.x pour solutions Experience Cloud](overview.md)
+ [Notes de mise à jour](rel-notes.md)
+ Prise en main {#getting-started-ios}
   + [Présentation de la prise en main](getting-started/getting-started.md)
   + [Avant de commencer](getting-started/requirements.md)
   + [Mise en œuvre principale et cycle de vie](getting-started/dev-qs.md)
   + [Règles de traitement et données contextuelles](getting-started/proc-rules.md)
   + [Intégration de Swift ](getting-started/swift-integration.md)
   + [Migration vers la bibliothèque iOS 4.x](getting-started/migration-v3.md)
+ Configuration {#config-ios}
   + [Présentation de la configuration](configuration/configuration.md)
   + [Fichier de configuration JSON ADBMobile](configuration/json-config/json-config.md)
   + [Remplacement du chemin du fichier de configuration JSON ADBMobile](configuration/json-config/json-config-remote.md)
   + [Traitement par lot des accès](configuration/hit-batching.md)
   + [Méthodes de configuration](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Mesures de cycle de vie](metrics.md)
+ Analytics {#analytics-ios}
   + [Présentation d’Analytics](analytics-main/analytics-main.md)
   + [Suivi des états d’application](analytics-main/states.md)
   + [Suivi des actions d’application](analytics-main/actions.md)
   + [Suivi des blocages d’application](analytics-main/crashes.md)
   + [Actions minutées](analytics-main/timed-actions.md)
   + [Valeur de durée de vie visiteur](analytics-main/lifetime-value.md)
   + Variable products{#products-variable}
      + [Variable products](analytics-main/products/products.md)
      + [Variable products avec des eVars de marchandisage et des événements spécifiques à un produit](analytics-main/products/products-variable-evars-events.md)
   + [Sérialisation d’événements](analytics-main/event-serialization.md)
   + [Chemin ](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Présentation des postbacks](analytics-main/postback/postback.md)
      + [Exemple de postback](analytics-main/postback/postback-example.md)
      + [Postbacks de type PII](analytics-main/postback/c-pii-postbacks.md)
   + [Méthodes Analytics](analytics-main/analytics-methods.md)
+ Acquisition {#acquisition-ios}
   + [Présentation de l’acquisition](acquisition-main/acquisition-main.md)
   + [Acquisition des applications mobiles](acquisition-main/acquisition.md)
   + [Méthodes d’acquisition](acquisition-main/c-acquisition-methods.md)
   + Suivi des liens profonds{#tracking-deep-links}
      + [Suivi des liens profonds](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Suivi de liens profonds différés tiers](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Évaluation de l’acquisition d’un lien marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Test de l’acquisition de V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Test de l’acquisition héritée](acquisition-main/t-testing-acquisition.md)
   + [Publicités Search Ads d’Apple](acquisition-main/c-apple-search-ads.md)
+ Messagerie {#messaging-ios}
   + [Présentation de la messagerie](messaging-main/messaging-main.md)
   + Messagerie in-app{#in-app-messaging}
      + [Messagerie in-app](messaging-main/messaging/messaging.md)
      + [Dépannage de la messagerie intégrée (in-app)](messaging-main/messaging/in-apps-ts.md)
   + Messagerie Push{#push-messaging}
      + [Messagerie Push](messaging-main/push-messaging/push-messaging.md)
      + [Mise en œuvre de la messagerie Push avec la création de liens profonds](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Réception de notifications push enrichies](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Résolution des problèmes liés aux messages push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Emplacement {#location-ios}
   + [Présentation de l’emplacement](location/location.md)
   + [Géolocalisation et points ciblés](location/geo-poi.md)
   + [Suivi iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Présentation de Target](target-main/target-main.md)
   + [Méthodes Target](target-main/c-target-methods.md)
   + [Prérécupération du contenu des offres dans iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Target Preview sous iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Présentation d’Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Méthodes de services d’identification Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Méthodes Audience Manager](amm/aam-methods.md)
+ Mise en œuvre de l’Apple TV avec tvOS {#apple-tv-implementation-tvos-ios}
   + [Mise en œuvre de l’Apple TV avec tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target pour TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Méthodes TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ Mise en œuvre de l’extension iOS {#ios-ext}
   + [Mise en œuvre de l’extension iOS ](ios-ext/ios-ext.md)
   + [Mise en œuvre d’une extension autonome ](ios-ext/c-stand-alone-extension-implementation.md)
+ [Mise en œuvre de l’Apple Watch avec WatchOS 2](apple-watch-implementation-watchkit.md)
+ Références relatives au SDK iOS {#sdk-reference-ios}
   + [Références relatives au SDK iOS ](reference/reference.md)
   + [ID d’application](reference/app-ids.md)
   + [Suivi des visiteurs entre une application et le web mobile](reference/hybrid-app.md)
   + [Versions des appareils iOS ](reference/device-versions.md)
+ Confidentialité et Règlement général sur la protection des données{#privacy-gdpr-ios}
   + [Confidentialité et Règlement général sur la protection des données](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Récupération des identifiants stockés](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Définition de l’état de souscription de l’utilisateur](c-mob-privacy-gdpr-ios/privacy.md)
+ Module externe PhoneGap {#phonegap-ios}
   + [Module externe PhoneGap](phonegap/phonegap.md)
   + [Méthodes du module externe PhoneGap](phonegap/phonegap-methods.md)

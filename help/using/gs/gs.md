---
description: Ces informations vous aident à comprendre et à utiliser Adobe Mobile Services.
keywords: mobile
seo-description: Ces informations vous aident à comprendre et à utiliser Adobe Mobile Services.
seo-title: Prise en main
solution: Experience Cloud,Analytics
title: Prise en main
topic: Metrics
uuid: a7ae7c5a-dab8-4603-b4cd-af73a2f09f71
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 15%

---


# Prise en main{#getting-started}

Ces informations vous aident à comprendre et à utiliser Adobe Mobile Services.

adobe Mobile Services se compose des éléments suivants :

* Interface utilisateur d’Adobe Mobile Services
* SDK Adobe Mobile

Pour les sociétés d’entreprise qui recherchent le moyen le plus efficace d’augmenter l’engagement des utilisateurs et de prouver le retour sur investissement (RSI) pour leur investissement dans les applications mobiles, l’Adobe fournit une solution de bout en bout, Adobe Mobile Services, pour acquérir et impliquer les utilisateurs des applications et analyser et optimiser leurs expériences.

Aujourd&#39;hui, le paysage des applications mobiles est considérablement différent de celui du premier lancement du smartphone. Avoir une application mobile pour connecter vos clients à votre marque ne suffit plus ; aujourd&#39;hui, vous devez désormais générer une expérience client cohérente et convaincante entre les canaux et utiliser votre application mobile comme point de contact stratégique pour attirer vos clients les plus fidèles et les plus rentables. Mais pour que ces utilisateurs puissent interagir avec votre application, il est nécessaire de disposer d’un contenu convaincant, de notifications contextuelles, d’une personnalisation intelligente, d’une analyse intégrée des applications, etc.

## Interface utilisateur d’Adobe Mobile Services {#mobile-services-ui}

L’interface utilisateur de Mobile Services est prise en charge sur les navigateurs suivants :

* Google Chrome (les deux dernières versions)
* Mozilla Firefox (les deux dernières versions)
* Apple Safari (les deux dernières versions)
* Microsoft Edge (les deux dernières versions)

Adobe Mobile Services contribue à stimuler l’engagement des utilisateurs des applications mobiles de la manière suivante :

### Acquérir

Dans *Acquire*, vous utilisez des médias payants, détenus et gagnés pour augmenter l’acquisition d’utilisateurs pour les téléchargements d’applications dans les principales boutiques d’applications. Grâce à Adobe Mobile Services, vous pouvez accélérer le processus d’acquisition des utilisateurs de l’application.

adobe Mobile Services fournit des workflows d’acquisition d’utilisateurs, notamment le suivi des acquisitions et les liens profonds, qui mesurent l’efficacité de vos canaux dans l’acquisition d’utilisateurs d’applications. Grâce aux liens marketing qui effectuent le suivi des utilisateurs issus de chaque canal, vous pouvez bénéficier d’une bonne visibilité sur les canaux les plus efficaces pour stimuler l’acquisition d’utilisateurs rentables et engagés.

En outre, avec des liens profonds, vous pouvez amener les utilisateurs directement dans le contenu de l’application que vous souhaitez voir et les encourager à installer votre application si nécessaire.

L’acquisition offre les principales fonctionnalités suivantes :

* Analyse des acquisitions pour les applications
* Suivi des liens dans les boutiques d’applications
* Liens profonds vers des applications
* Intégration de post-back aux réseaux publicitaires

Pour plus d’informations sur cette phase, voir [Acquisition](/help/using/acquisition-main/acquisition-main.md).

### Analyser

Dans *Analyser*, vous pouvez comprendre comment les consommateurs utilisent l’application mobile et ce qui les fait convertir ou revenir.

Avec Adobe Analytics, vous pouvez obtenir des informations clés sur la façon dont les utilisateurs téléchargent, installent et ouvrent votre application. Vous pouvez également mesurer et analyser le contenu et l’interface utilisateur de votre application, effectuer des analyses de cohorte, le cheminement et les abandons. Adobe Analytics vous permet d’utiliser une banque de données centrale pour prendre vos décisions marketing et réduire les silos de données marketing dans votre entreprise.

Vous pouvez utiliser Adobe Audience Manager pour enrichir vos segments d’audience de données riches afin de fournir des expériences plus contextuelles et personnelles.

*Analyser* les offres en utilisant les fonctions clés suivantes :

* Analyse de l’engagement des applications
* Analyse du cheminement et de l’entonnoir
* Analyse de cohorte et de rétention
* Analyse des emplacements
* Prise en charge étendue des périphériques et plates-formes

Pour plus d’informations sur les rapports que vous pouvez exécuter afin d’analyser vos clients, voir [Rapports](/help/using/usage/usage.md).

### Interagir

Dans *Interagir*, vous pouvez utiliser des notifications Push et des messages in-app pertinents pour communiquer avec vos utilisateurs. Grâce aux notifications Push ciblées et à la messagerie in-app, vous pouvez vous assurer que les utilisateurs continuent à revenir à votre application. Avec la prise en charge des segments d’Analytics, vous pouvez cible vos notifications Push aux segments d’utilisateurs qui répondront et augmenteront leur propension à la conversion.

*Engagez* les offres à utiliser les fonctionnalités clés suivantes :

* Les notifications Push sont déclenchées par les segments d’analyse.
* Les messages in-app sont déclenchés par les analyses en temps réel, les alertes et les nouvelles offres/contenus.
* Comprendre les vues, les taux de clics publicitaires et le comportement en aval

### Messagerie Adobe Mobile

Vous pouvez utiliser les notifications Push et In-App pour communiquer avec vos utilisateurs. Les notifications Push sont envoyées via le système d’exploitation sur l’appareil, tandis que les messages in-app sont envoyés dans l’application lorsqu’un utilisateur interagit activement avec l’application. Les messages in-app peuvent généralement inclure divers formats supplémentaires, tels que des fenêtres contextuelles et des spots.

Dans Adobe Mobile, vous pouvez configurer les types de messages suivants :

**Les notifications** Push, qui apparaissent en dehors de votre application, offre les fonctionnalités suivantes :

* Encouragez le réengagement au moyen de notifications Push pertinentes.
* Créez, segmentez et envoyez des messages aux clients qui ont téléchargé l’application d’une marque et ont accepté de recevoir des notifications Push par le biais de la souscription.
* Sont envoyées côté serveur par les boutiques d’applications plutôt que depuis l’application mobile.

Pour plus d’informations sur la création de notifications push, voir [Création d’un message push](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

**Les notifications** intégrées à l’application offre les fonctionnalités suivantes :

* Amenez les utilisateurs à une action spécifique lorsqu’ils se trouvent dans la session de l’application.
* Formats supplémentaires (alerte, plein écran) car les messages sont diffusés par l’application, plutôt qu’un réseau de diffusions Push.
* sont déclenchées par des analyses en temps réel.
* Autorisez les promotions croisées d’applications et de produits.
* Encouragez les utilisateurs à quitter la boutique d’applications.
* Diffuser des messages en temps réel et basés sur l’emplacement

Pour plus d’informations sur la création de messages in-app, voir [Création d’un message in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).

### Optimiser

Dans *Optimiser*, vous pouvez optimiser les conversions (abonnements, commerce, recettes publicitaires, etc.) et améliorer la fidélisation des clients. L’optimisation de l’expérience utilisateur dans votre application peut vous aider à personnaliser votre contenu afin d’augmenter le retour sur investissement et la conversion.

Pour plus d’informations sur les tests et sur Adobe Target, consultez la section [Adobe Target](https://docs.adobe.com/content/help/fr-FR/target/using/target-home.html).

### Géociblage

Un périphérique mobile vous permet de déterminer par nature où se trouve un client lorsqu’il communique avec votre application ou de le faire tourner en arrière-plan par l’intermédiaire du GPS. Grâce au géociblage, Adobe Target vous permet de diffuser du contenu, des offres ou des messages adaptés et pertinents à un moment où la proximité est importante. Vous pouvez cible les utilisateurs qui se trouvent dans un rayon défini d’un point ciblé ou qui se trouvent à proximité d’iBeacons et qui reçoivent des notifications Push appropriées.

Les applications Adobe Target for Mobile tirent désormais pleinement parti de la segmentation et du rapports améliorés disponibles via Adobe Analytics. Cela signifie que Adobe Target peut tirer parti de toutes les mesures d’application clés d’Analytics en les utilisant pour la cible et la personnalisation ; il permet également un niveau de rapports plus élevé sur la réussite des tests, ce qui permet aux spécialistes du marketing de mieux comprendre les questions &quot;et si&quot;, des réponses qui peuvent éviter que le spécialiste du marketing de l’application ne soit contraint de faire des investissements dans l’application. L’intégration d’Analytics/Cible for apps permet de proposer une offre combinée, qui représente la solution d’engagement d’application la plus robuste disponible sur le marché.

Pour plus d’informations sur l’emplacement, voir le contenu suivant :

* [Emplacement dans le guide de l’utilisateur Mobile Services](/help/using/location/c-location-overview.md)
* [Emplacement dans le guide SDK Android](/help/android/location/location.md)
* [Emplacement dans le guide SDK iOS](/help/ios/location/location.md)

## SDK Adobe Mobile {#mobile-services-sdk}

adobe fournit une solution de marketing mobile de bout en bout qui accélère l’engagement de vos clients dans toutes ces zones. Avec un seul SDK, vous pouvez accéder aux fonctionnalités d’Adobe Analytics, Adobe Campaign et Adobe Audience Manager, ce qui réduit le coût technique de la gestion de plusieurs SDK différents.

L’Adobe Mobile SDK offre les fonctionnalités suivantes :

* Engagement mobile de bout en bout

   Vous pouvez mesurer et optimiser des applications sur plusieurs plates-formes à l’aide d’un seul kit SDK mobile Adobe intégré, léger et léger.
* Acquérir de nouveaux clients et offrir des micro-moments attrayants

   * Ramenez les utilisateurs dans votre application encore et encore par le biais de notifications Push ciblées, notamment la prise en charge des médias enrichis et la messagerie in-app.
   * Utilisez des liens profonds pour pousser les utilisateurs de l’application directement dans le contenu que vous souhaitez.

* Mesurer et optimiser les expériences pour générer un retour sur investissement

   Vous pouvez obtenir des informations sur les mesures de cycle de vie des applications, notamment l’analyse des entonnoirs (téléchargements, installations, ouvertures), les actions incluant la durée de session, les blocages, les balises et les interactions de messagerie.
* Complet

   * Prise en charge étendue des principaux systèmes d’exploitation mobiles et des outils de développement multiplateformes.
   * Prise en charge étendue des périphériques sur les smartphones, tablettes, portables et consoles OTT (par-dessus tout).

* Intégré

   * Un SDK pour plusieurs solutions (Analytics, Campaign et Audience Manager), ce qui réduit le temps et les efforts de mise en oeuvre pour les développeurs.
   * Une seule ligne de code est nécessaire pour collecter les mesures de cycle de vie des applications de &quot;base&quot;.
   * Au fur et à mesure que vous développez votre stratégie mobile, vous pouvez facilement activer les fonctionnalités Adobe Experience Cloud pour acquérir, analyser et impliquer les utilisateurs.

* Rapide et léger

   * Réduit la charge de traitement du périphérique pour l’envoi de données aux serveurs d’Adobe et aux systèmes tiers.
   * L’encombrement réduit la taille du package d’application envoyé aux boutiques d’applications.

For more information about the Adobe Mobile SDKs, see [Android SDK 4.x for Experience Solutions](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/overview.html) and [iOS SDK 4.x for Experience Cloud Solutions](https://docs.adobe.com/content/help/fr-FR/mobile-services/ios/rel-notes.html).

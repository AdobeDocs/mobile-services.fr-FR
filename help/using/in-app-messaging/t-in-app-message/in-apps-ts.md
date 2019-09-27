---
description: Ces informations peuvent vous aider à résoudre les problèmes liés à la messagerie in-app.
keywords: mobile
seo-description: Ces informations peuvent vous aider à résoudre les problèmes liés à la messagerie in-app.
seo-title: Dépannage de la messagerie intégrée (in-app)
solution: Marketing Cloud,Analytics
title: Dépannage de la messagerie intégrée (in-app)
topic: Mesures
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Ces informations peuvent vous aider à résoudre les problèmes liés à la messagerie in-app.

Si vous réalisez toutes les exigences relatives à la messagerie in-app, mais que les messages ne s’affichent pas, vérifiez les éléments suivants :

## Placez-vous la nouvelle configuration et le nouveau SDK dans l’application ?

* Vérifiez que la version du SDK est 4.2 ou supérieure et que ce dernier est correctement configuré.

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Mon message en plein écran ne s’affiche pas sous Android. J’utilise le SDK et la configuration appropriés et mes déclencheurs sont respectés.

Avez-vous mis à jour votre fichier de manifeste afin de définir l’activité Plein écran ?

## Mon message de notification locale ne fonctionne pas sous Android.

Assurez-vous que le récepteur de diffusion de notifications locales est déclaré dans votre manifeste. For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## Le message est-il actif ?

Consultez la vue Liste dans la colonne **[!UICONTROL État]** de la page Gérer les messages in-app et vérifiez que le message est actif.

## Regardez *afficher une fois*, *afficher toujours*, *afficher les paramètres hors ligne* sur la page Audience.

Vérifiez que ces paramètres sont corrects. Sur la page Audience, consultez les options de l’onglet **Déclencheur**, dans lequel vous pouvez indiquer la fréquence d’affichage du message.

## En cas d’utilisation d’un événement de lancement comme déclencheur…

Le lancement se déclenche uniquement en cas de nouvelle session. Pour plus d’informations sur le moment où commence une session, voir `lifecycleTimeout` dans le fichier de configuration [JSON](/help/ios/configuration/json-config/json-config.md) ADBMobile.

## J’ai mis à jour mon message à distance, mais mon application affiche toujours l’ancien message.

Procédez de l’une des manières suivantes :

* Il peut s’écouler quelques minutes avant que la gestion dynamique des balises ne mette à jour son point de terminaison avec votre nouvelle définition.

   Patientez et essayez à nouveau.

* La configuration se mettra à jour uniquement lors d’un nouveau lancement.

   Si l’application a été redémarrée pendant le délai d’expiration de la session du cycle de vie, la nouvelle configuration n’a peut-être pas été téléchargée.

## Mon image ne correspond pas exactement à l’espace fourni par le modèle.

Le modèle de message in-app en plein écran prend en charge l’affichage d’une image provenant d’un serveur distant (adresse URL de l’image) ou du lot d’applications (image en lot). L’image doit être spécifiée dans un format standard tel que JPG, GIF ou PNG.

Du fait que les écrans des appareils peuvent être de taille très variable, l’image ne tiendra probablement pas exactement dans l’espace prévu par le modèle. Le modèle s’efforce de toujours afficher le centre de l’image et les recadre (portrait) ou atténue (paysage) les bords si l’image ne s’adapte pas au format de l’écran.

Les règles de dimensionnement et de placement exactes pour chaque orientation sont les suivantes :

* **Portrait :** image mise à l’échelle à une hauteur de 195 pixels pour les téléphones, 529 pixels pour les tablettes, centrée si la largeur de l’image est inférieure à la largeur de l’appareil, recadrée si la largeur de l’image est supérieure à la largeur de l’appareil.

* **Paysage :** image mise à l’échelle à 100 % de la hauteur de l’appareil, largeur égale à 75 % de celle de l’appareil, avec une apparition en fondu sur la droite.

   Si vous rencontrez des problèmes avec le modèle Plein écran, vous pouvez télécharger et utiliser le modèle HTML personnalisé. Le modèle HTML personnalisé offre davantage de flexibilité pour les images et permet un contrôle complet du modèle.

## Mes messages ne reflètent pas les modifications ou mises à jour que j’ai apportées dans l’interface utilisateur.

Le SDK récupère les messages nouveaux ou mis à jour au moment du lancement d’un cycle de vie. Ceci se produit seulement quand l’application est fermée/placée en arrière-plan pendant un délai plus long que la valeur de temporisation, avant d’être rouverte.

Procédez comme suit :

1. Traitez l’URL de vos messages dans votre fichier de configuration pour vérifier que le message distant est mis à jour (par exemple, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`).
1. Fermez l’application.
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. Ouvrez l’application, naviguez jusqu’à l’emplacement où doit s’afficher le message, puis vérifiez qu’il a été mis à jour.
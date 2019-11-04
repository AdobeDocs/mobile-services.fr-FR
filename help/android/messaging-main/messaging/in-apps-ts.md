---
description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
keywords: mobile
seo-description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
seo-title: Dépannage de la messagerie intégrée (in-app)
solution: Experience Cloud,Analytics
title: Dépannage de la messagerie intégrée (in-app)
topic: Mesures
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
translation-type: ht
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Dépannage de la messagerie intégrée (in-app){#troubleshooting-in-app-messaging}

Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.

Si vous avez respecté toutes les exigences relatives à la messagerie intégrée (in-app), mais que les messages ne s’affichent pas, vérifiez les éléments suivants :

## Placez-vous la nouvelle configuration et le nouveau SDK dans l’application ?

Assurez-vous que votre configuration comporte une section [Messagerie](/help/android/messaging-main/messaging/messaging.md) (fichier JSON téléchargé) ou un point de terminaison distant Message afin qu’il puisse être récupéré depuis la gestion dynamique des balises.

## Mon message en plein écran ne s’affiche pas sous Android. J’utilise le SDK et la configuration appropriés et mes déclencheurs sont respectés.

Avez-vous mis à jour votre fichier de manifeste afin de définir l’activité Plein écran ?

## Mon message de notification locale ne fonctionne pas sous Android.

Assurez-vous que le récepteur de diffusion de notifications locales est déclaré dans votre manifeste. Pour obtenir plus d’informations, voir l’étape 2 *Activation de la messagerie in-app* dans [Messagerie in-app](/help/android/messaging-main/messaging/messaging.md).

## Le message est-il actif ?

Pour vérifier si le message est actif, sur la page Manage In-App Message (Gérer le message in-app), dans la colonne **[!UICONTROL Status]** (État), vérifiez la liste des messages.

## Consultez les paramètres *afficher une fois*, *afficher toujours*, *afficher hors ligne* dans l’onglet Audience.

Vérifiez que ces paramètres sont définis comme vous le souhaitez. Sous l’onglet **[!UICONTROL Audience]**, vérifiez vos options **[!UICONTROL Déclencheur]**, qui vous permettent de définir la fréquence d’affichage du message.

## En cas d’utilisation d’un événement de lancement comme déclencheur…

Le lancement se déclenche uniquement en cas de nouvelle session. Pour obtenir plus d’informations sur le début d’une session, voir la ligne `lifecycleTimeout` du fichier de configuration [JSON](/help/android/configuration/json-config/json-config.md).

## J’ai mis à jour mon message à distance, mais mon application affiche toujours l’ancien message.

À noter :

* La gestion dynamique des balises peut nécessiter quelques minutes pour mettre à jour son point de terminaison avec votre nouvelle définition. Patientez quelques minutes et réessayez.
* La configuration ne se mettra à jour que lors d’un nouveau lancement. Si l’application a été redémarrée pendant le délai d’expiration de la session du cycle de vie, la nouvelle configuration n’a peut-être pas été téléchargée.

Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

## Mon image ne correspond pas exactement à l’espace fourni par le modèle.

Le modèle de message intégré (in-app) en plein écran prend en charge l’affichage d’une image provenant d’un serveur distant (adresse URL de l’image) ou du lot d’applications (image en lot). L’image doit être spécifiée dans un format standard tel que JPG, GIF ou PNG. Puisque les écrans des appareils peuvent être de taille très variable, l’image ne tiendra probablement pas exactement dans l’espace prévu par le modèle. Le modèle se focalise sur l’affichage du centre de l’image et, si l’image ne tient pas dans l’espace prévu, rognez (portrait) ou estompez (paysage) les bords.

Les règles de dimensionnement et de placement exactes pour chaque orientation sont les suivantes :

* **Portrait**
   * Hauteur de 195 px pour les téléphones.
   * Hauteur de 529 px pour les tablettes.
   * Centrée si la largeur de l’image est plus petite que la largeur de l’appareil.
   * Rognée si la largeur de l’image est plus grande que la largeur de l’appareil.

* **Paysage**
   * L’image s’adapte à 100 % à la hauteur de l’appareil.
   * La largeur correspond à 75 % à celle de l’appareil, avec un fondu sur la droite.
   Si vous rencontrez des problèmes avec le modèle Plein écran, vous pouvez télécharger et utiliser le modèle HTML personnalisé. Ce dernier offre davantage de flexibilité pour les images et permet un contrôle complet du modèle.


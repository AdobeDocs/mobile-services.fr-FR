---
description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
keywords: mobile
seo-description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
seo-title: Dépannage de la messagerie intégrée (in-app)
solution: Marketing Cloud,Analytics
title: Dépannage de la messagerie intégrée (in-app)
topic: Mesures
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.

Si vous avez respecté toutes les exigences relatives à la messagerie intégrée (in-app), mais que les messages ne s’affichent pas, vérifiez les éléments suivants :

## Placez-vous la nouvelle configuration et le nouveau SDK dans l’application ?

Vérifiez que la version du SDK est 4.2 ou supérieure et que le SDK est correctement configuré. Assurez-vous que votre configuration comporte une section `Messages` (fichier JSON téléchargé) ou un point de terminaison distant Message afin qu’il puisse être récupéré depuis la gestion dynamique des balises.

## Mon message en plein écran ne s’affiche pas sous Android. J’utilise le SDK et la configuration appropriés et mes déclencheurs sont respectés.

Avez-vous mis à jour votre fichier de manifeste afin de définir l’activité Plein écran ?

## Mon message de notification locale ne fonctionne pas sous Android.

Assurez-vous que le récepteur de diffusion de notifications locales est déclaré dans votre manifeste. For more information, see step 2 in [Enabling In-App Messages](/help/android/messaging-main/messaging/messaging.md).

## Le message est-il actif ?

Consultez la vue Liste de la page Gérer les messages in-app, dans la colonne État, et vérifiez que le message est actif.

## Regardez *afficher une fois*, *afficher toujours*, *afficher les paramètres hors ligne* sur l’onglet Audience.

Vérifiez que ces paramètres sont définis comme vous le souhaitez. Sous l’onglet **[!UICONTROL Audience]**, vérifiez vos options **Déclencheur], qui vous permettent de définir la fréquence d’affichage du message.[!UICONTROL **

## En cas d’utilisation d’un événement de lancement comme déclencheur…

Le lancement se déclenche uniquement en cas de nouvelle session. For more information about when a session begins, see the `lifecycleTimeout` row in the JSON Config file. For more information, see  ADBMobile JSON Config.[](/help/ios/configuration/json-config/json-config.md)

## J’ai mis à jour mon message à distance, mais mon application affiche toujours l’ancien message.

Effectuez l’une des tâches suivantes :

* Il peut s’écouler quelques minutes avant que la gestion dynamique des balises ne mette à jour son point de terminaison avec votre nouvelle définition.

   Patientez quelques minutes et réessayez.

* La configuration se mettra à jour uniquement lors d’un nouveau lancement.
Si l’application a été redémarrée pendant le délai d’expiration de la session du cycle de vie, la nouvelle configuration n’a peut-être pas été téléchargée.

   Pour plus d’informations, voir [Mesures de cycle de vie](/help/ios/metrics.md).

## Mon image ne correspond pas exactement à l’espace fourni par le modèle.

Le modèle de message intégré (in-app) en plein écran prend en charge l’affichage d’une image provenant d’un serveur distant (adresse URL de l’image) ou du lot d’applications (image en lot). L’image doit être spécifiée dans un format standard tel que JPG, GIF ou PNG.

Puisque les écrans des appareils peuvent être de taille très variable, l’image ne tiendra probablement pas exactement dans l’espace prévu par le modèle. Le modèle se focalise sur l’affichage du centre de l’image et, si l’image ne tient pas dans l’espace prévu, rognez (portrait) ou estompez (paysage) les bords.

Les règles de dimensionnement et de placement exactes pour chaque orientation sont les suivantes :

* **Portrait**:
   * Hauteur de 195 px pour les téléphones.
   * Hauteur de 529 px pour les tablettes.
   * Centrée si la largeur de l’image est plus petite que la largeur de l’appareil.
   * Rognée si la largeur de l’image est plus grande que la largeur de l’appareil.

* **Paysage**:
   * L’image s’adapte à 100 % à la hauteur de l’appareil.
   * La largeur correspond à 75 % à celle de l’appareil, avec un fondu sur la droite.

Si vous rencontrez des problèmes avec le modèle Plein écran, vous pouvez télécharger et utiliser le modèle HTML personnalisé. Ce dernier offre davantage de flexibilité pour les images et permet un contrôle complet du modèle.

## Sur un iPhone X, les messages in-app ne s’affichent pas en mode Plein écran.

Pour afficher les messages in-app en mode Plein écran sur un iPhone X, procédez comme suit :

1. Add `viewport-fit=cover` in the meta tag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Paramétrez la marge intérieure appropriée dans la feuille de style CSS pour les éléments d’IU du haut, par exemple :

   ```html
   topelement {
     padding-top:20px;
     /*Status bar height on iOS 11.0*/
     padding-top:constant(safe-area-inset-top);
     /*Status bar height on iOS 11+ */
     padding-top:env(safe-area-inset-top);
     } 
   ```

   Ces paramètres empêchent les éléments de l’IU d’entrer en collision avec la barre d’état.

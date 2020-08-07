---
description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
keywords: mobile
seo-description: Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.
seo-title: Dépannage de la messagerie intégrée (in-app)
solution: Marketing Cloud,Analytics
title: Dépannage de la messagerie intégrée (in-app)
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 53%

---


# Dépannage de la messagerie intégrée (in-app){#troubleshooting-in-app-messaging}

Ces informations vous aideront à résoudre les problèmes liés à la messagerie in-app.

Si vous avez satisfait à toutes les exigences relatives à la messagerie in-app, mais que les messages ne s’affichent pas, vérifiez les éléments suivants :

## Placez-vous la nouvelle configuration et le nouveau SDK dans l’application ?

Vérifiez que le SDK est de la version 4.2 ou supérieure et qu’il est correctement configuré. Assurez-vous que votre configuration comporte une section `Messages` (fichier JSON téléchargé) ou un point de terminaison distant Message afin qu’il puisse être récupéré depuis la gestion dynamique des balises.

## Mon message en plein écran sous Android ne s’affiche pas. J’utilise le SDK, la configuration et mes déclencheurs sont respectés.

Avez-vous mis à jour votre fichier manifeste pour définir l&#39;activité en plein écran ?

## Mon message de notification locale sous Android ne fonctionne pas.

Assurez-vous que le récepteur de diffusion de notifications locales est déclaré dans votre manifeste. Pour obtenir plus d’informations, voir l’étape 2 [Activation des messages in-app](/help/android/messaging-main/messaging/messaging.md).

## Le message est-il actif ?

Vérifiez la vue de liste sur la page Gérer les messages in-app de la colonne État et si elle est active.

## Consultez les paramètres *afficher une fois*, *afficher toujours*, *afficher hors ligne* dans l’onglet Audience.

Vérifiez que ces paramètres sont définis comme vous le souhaitez. Sous l’onglet **[!UICONTROL Audience]**, vérifiez vos options **[!UICONTROL Déclencheur]**, qui vous permettent de définir la fréquence d’affichage du message.

## Si vous utilisez le événement de lancement comme déclencheur...

Le lancement se déclenche uniquement en cas de nouvelle session. Pour obtenir plus d’informations sur le début d’une session, voir la ligne `lifecycleTimeout` du fichier de configuration JSON. Pour plus d’informations, voir [Configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

## J’ai mis à jour mon message à distance mais mon application affiche toujours l’ancien message.

Procédez de l’une des manières suivantes :

* La gestion dynamique des balises peut nécessiter quelques minutes pour mettre à jour son point de terminaison avec votre nouvelle définition.

   Patientez quelques minutes et réessayez.

* La configuration se mettra à jour uniquement lors d’un nouveau lancement. 
Si l’application a été redémarrée pendant le délai d’expiration de la session du cycle de vie, la nouvelle configuration n’a peut-être pas été téléchargée.

   Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/ios/metrics.md).

## Mon image ne correspond pas exactement à l’espace fourni par le modèle.

Le modèle de message intégré en plein écran prend en charge l’affichage d’une image à partir d’un serveur distant (URL d’image) ou du lot d’applications (image groupée). L’image doit être spécifiée dans un format standard tel que JPG, GIF ou PNG.

Puisque les écrans des appareils peuvent être de taille très variable, l’image ne tiendra probablement pas exactement dans l’espace prévu par le modèle. Le modèle se focalise sur l’affichage du centre de l’image et, si l’image ne tient pas dans l’espace prévu, rognez (portrait) ou estompez (paysage) les bords.

Les règles de dimensionnement et de placement exactes pour chaque orientation sont les suivantes :

* **Portrait** :
   * Hauteur de 195 px pour les téléphones
   * Hauteur de 529 px pour les tablettes
   * Centré si la largeur de l’image est inférieure à la largeur du périphérique.
   * Recadré si la largeur de l’image est supérieure à la largeur du périphérique.

* **Paysage** :
   * L’image est mise à l’échelle à 100 % de la hauteur du périphérique.
   * La largeur est de 75 % du périphérique, avec un fondu en dehors sur la droite.

Si vous rencontrez des problèmes avec le modèle plein écran, vous pouvez télécharger et utiliser le modèle HTML personnalisé. Ce modèle offre davantage de flexibilité pour les images et permet un contrôle total du modèle.

## Les messages in-app sur un iPhone X ne s’affichent pas en mode plein écran.

Pour afficher des messages in-app en mode plein écran sur un iPhone X :

1. Ajoutez `viewport-fit=cover` dans la balise meta.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configurez le remplissage approprié dans le fichier CSS pour l’élément d’interface utilisateur supérieur, tel que :

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   Ces paramètres empêchent les éléments de l’interface d’entrer en collision avec la barre d’état.

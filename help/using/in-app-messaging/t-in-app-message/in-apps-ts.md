---
description: Ces informations peuvent vous aider à résoudre les problèmes liés à la messagerie in-app.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Dépannage de la messagerie intégrée (in-app)
topic-fix: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
exl-id: 6be5beef-3bde-49f8-9ec0-c5d32bd43045
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 100%

---

# Dépannage de la messagerie intégrée (in-app) {#troubleshooting-in-app-messaging}

{#eol}

Ces informations peuvent vous aider à résoudre les problèmes liés à la messagerie in-app.

Si vous avez satisfait à toutes les exigences relatives à la messagerie in-app, mais que les messages ne s’affichent pas, vérifiez les éléments suivants :

## Placez-vous la nouvelle configuration et le nouveau SDK dans l’application ?

* Vérifiez que la version du SDK est 4.2 ou supérieure et que ce dernier est correctement configuré.

* Assurez-vous que votre configuration comporte une section [Messagerie](/help/using/in-app-messaging/in-app-messaging.md) (fichier JSON téléchargé) ou un point d’entrée distant Messages afin qu’il puisse être récupéré depuis la gestion dynamique des balises.

## Mon message en plein écran sous Android ne s’affiche pas. J’utilise le SDK et la configuration appropriés et mes déclencheurs sont respectés.

Avez-vous mis à jour votre fichier manifeste pour définir l’activité en plein écran ?

## Mon message de notification locale sous Android ne fonctionne pas.

Assurez-vous que le récepteur de diffusion de notifications locales est déclaré dans votre manifeste.

## Le message est-il actif ?

Consultez la vue Liste dans la colonne **[!UICONTROL État]** de la page Gérer les messages in-app et vérifiez que le message est actif.

## Consultez les paramètres *afficher une fois*, *afficher toujours*, *afficher hors ligne* sur la page Audience.

Vérifiez que ces paramètres sont corrects. Sur la page Audience, consultez les options de l’onglet **[!UICONTROL Déclencheur]**, dans lequel vous pouvez indiquer la fréquence d’affichage du message.

## En cas d’utilisation d’un événement de lancement comme déclencheur…

Le lancement se déclenche uniquement en cas de nouvelle session.

## J’ai mis à jour mon message à distance, mais mon application affiche toujours l’ancien message.

Procédez de l’une des manières suivantes :

* La gestion dynamique des balises peut nécessiter quelques minutes pour mettre à jour son point d’entrée avec votre nouvelle définition.

   Patientez quelques minutes et réessayez.

* La configuration se mettra à jour uniquement lors d’un nouveau lancement.

   Si l’application a été redémarrée pendant le délai d’expiration de la session du cycle de vie, la nouvelle configuration n’a peut-être pas été téléchargée.

## Mon image ne correspond pas exactement à l’espace fourni par le modèle.

Le modèle de message in-app en plein écran prend en charge l’affichage d’une image à partir d’un serveur distant (URL d’image) ou du lot d’applications (image groupée). L’image doit être spécifiée dans un format standard tel que JPG, GIF ou PNG.

Puisque les écrans des appareils peuvent être de taille très variable, l’image ne tiendra probablement pas exactement dans l’espace prévu par le modèle. Le modèle se concentre toujours sur l’affichage du centre de l’image et rogne (portrait) ou atténue (paysage) les côtés si l’image est trop grande.

Les règles de dimensionnement et de placement exactes pour chaque orientation sont les suivantes :

* **Portrait**, où l’image est mise à l’échelle à une hauteur de 195 px pour le téléphone, de 529 px pour la tablette, centrée si la largeur de l’image est inférieure à la largeur de l’appareil et rognée si la largeur de l’image est supérieure à la largeur de l’appareil.

* **Paysage**, où l’image est mise à l’échelle à 100 % de la hauteur de l’appareil, largeur égale à 75 % de l’appareil et avec un fondu sur la droite.

   Si vous rencontrez des problèmes avec le modèle plein écran, vous pouvez télécharger et utiliser le modèle HTML personnalisé. Ce modèle offre davantage de flexibilité pour les images et permet un contrôle total du modèle.

## Mes messages ne reflètent pas les modifications/mises à jour que j’ai effectuées dans l’interface utilisateur.

Le SDK récupère les messages nouveaux ou mis à jour au moment du lancement d’un cycle de vie. Cette action est effectuée uniquement lorsque l’application est fermée/mise en arrière-plan pour une durée supérieure à la valeur du délai d’expiration du cycle de vie, puis rouverte.

Procédez comme suit :

1. Traitez l’URL de vos messages dans votre fichier de configuration pour vérifier que le message distant est mis à jour (par exemple, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`).
1. Fermez l’application.
1. Patientez pendant un délai plus long que la valeur `lifecycleTimeout` dans le fichier de configuration.
1. Ouvrez l’application, naviguez jusqu’à l’emplacement où doit s’afficher le message, puis vérifiez qu’il a été mis à jour.

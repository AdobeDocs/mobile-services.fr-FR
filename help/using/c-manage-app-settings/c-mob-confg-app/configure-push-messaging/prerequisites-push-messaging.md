---
description: Avant de pouvoir configurer la messagerie push dans les applications, vous devez effectuer certaines tâches.
keywords: mobile
seo-description: Avant de pouvoir configurer la messagerie push dans les applications, vous devez effectuer certaines tâches.
seo-title: Conditions préalables requises pour activer la messagerie push
solution: Marketing Cloud, Analytics
title: Conditions préalables requises pour activer la messagerie push
topic: Mesures
uuid: 194 e 6 e 07-b 794-4152-a 838-a 4125 c 3292 d 4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Prerequisites to enable push messaging {#prerequisites-to-enable-push-messaging}

Vous devez effectuer ces tâches avant de configurer la messagerie Push dans vos applications.

## Activation de Experience Cloud pour votre entreprise

Experience Cloud doit être activé pour votre entreprise Adobe Analytics. Vous pouvez vérifier l'état de votre gestionnaire de compte Adobe.

## Installation et configuration du SDK Mobile

* **Installation du SDK Mobile**

   Pour configurer la messagerie Push, vous devez télécharger et installer au moins la version 4.6 ou ultérieure du SDK Mobile. For more information, see [Download the SDKs](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **Configuration des services Push**

   Vous devez configurer les services push dans le SDK Mobile.
Pour plus d’informations, voir la vidéo et les rubriques suivants :

   * [Messagerie Push dans Android](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [Messagerie Push dans ios](/help/ios/messaging-main/push-messaging/push-messaging.md)

## Connectez-vous au service principal Mobile à l’aide de votre Adobe ID

>[!IMPORTANT]
>
>Pour utiliser la fonctionnalité de services Push, les utilisateurs doivent se connecter au service principal Mobile en utilisant leur Adobe ID et leur compte Analytics doit être associé à leur Adobe ID. La fonctionnalité de services push est indisponible si les utilisateurs se connectent par le biais de leur compte Adobe Analytics existant.

Si certains utilisateurs ne possèdent pas d’Adobe ID, effectuez les étapes suivantes :

1. (**Experience Cloud Administrator**) Invite users to the Experience Cloud.

1. (**User**) Create a personal Adobe ID using the instructions that you received from the Experience Cloud administrator.

   Un message électronique est automatiquement envoyé à chaque utilisateur une fois que l’administrateur a accompli l’étape précédente.

1. (**Users**) Log in to Mobile using their Adobe ID.

## Liaison des comptes d'utilisateurs dans le cloud Experience Cloud

Chaque utilisateur doit lier le compte de la solution Analytics depuis l’organisation Experience Cloud.

1. Pour vous connecter à Experience Cloud à l’aide d’un Adobe ID, saisissez [https://marketing.adobe.com](https://marketing.adobe.com) dans un navigateur.

1. Dans le coin supérieur droit, sélectionnez le nom de la société Analytics.

1. Cliquez sur **[!UICONTROL Ajouter l’organisation]**, puis sélectionnez **Adobe SiteCatalyst/Adobe Social]dans la liste déroulante.[!UICONTROL **

1. Saisissez le nom de la société et vos anciennes informations d’identification pour la société en question, puis cliquez sur **[!UICONTROL Lier le compte]**.

   L’Adobe ID est maintenant associé à votre compte Analytics, votre société et vos informations de connexion.

Pour plus d’informations, voir [Dépannage de la liaison de compte](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html).

## Configuration des services Push et du service d'ID de SDK dans l'interface utilisateur mobile

La section **[!UICONTROL Services push]est désactivée tant que vous n’avez pas activé le service d’identification pour votre application.** Mais, après avoir activé le service d'ID, la section Push Services est activée. Pour plus d'informations sur l'activation des services Push, voir [Configuration des options du service SDK ID](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md).

>[!IMPORTANT]: Vous devez cliquer **[!UICONTROL sur Enregistrer]** pour enregistrer vos modifications et actualiser les services Push.
>
>Vous pouvez configurer une application de la boutique d’applications pour Apple et une pour Google dans chaque suite de rapports. Si vous avez besoin d’applications supplémentaires, par exemple, une pour l’environnement de production et une pour l’environnement de développement, configurez une nouvelle application de la boutique d’applications et une nouvelle suite de rapports pour chaque environnement.

* Pour **Apple**, effectuez un glisser-déposer de votre clé privée et/ou de votre certificat. Si votre clé privée est chiffrée par un mot de passe, saisissez ce dernier.

   * Pour la **clé privée**, effectuez un glisser-déposer de votre clé privée dans la case.

      Vous pouvez également cliquer sur **[!UICONTROL Parcourir]pour sélectionner le fichier.** Ce fichier contient la clé privée. The certificate might also be included in this file (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * Pour le **mot de passe de clé privée**, si votre fichier de clé privée est chiffré, saisissez le mot de passe.

      (Conditionnel) Pour le **certificat**, effectuez un glisser-déposer de votre fichier de certificat dans la case. Vous pouvez également cliquer sur **[!UICONTROL Parcourir]pour sélectionner le fichier.** This field is not required if the private-key file also contains the certificate ( `.cert`, `.cer`, `.crt`, `.pem`).

* Pour **Google**, spécifiez la clé d’API de l’application.

   Cliquez sur **[!UICONTROL Tester]pour vérifier que l’application et Mobile Services sont configurés correctement.** Cette option est utile en cas de débogage et de dépannage.

   Saisissez les jetons push des appareils auxquels vous souhaitez envoyer le message. Vous pouvez envoyer le message vers plusieurs périphériques en spécifiant les jetons dans une liste séparée par des virgules.

   ![message de test Push](assets/push_test_list.png)

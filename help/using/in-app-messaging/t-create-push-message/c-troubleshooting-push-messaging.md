---
description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
keywords: mobile
seo-description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
seo-title: Résolution des problèmes liés aux messages push
solution: Marketing Cloud, Analytics
title: Résolution des problèmes liés aux messages push
topic: Mesures
uuid: c 7 be 4 ab 7-0 cfe -4296-84 a 8-01412 f 4 fd 93 f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* **Attente des accès Analytics**

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. Par défaut, ce traitement a lieu toutes les heures.

   Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. À titre d’exemple, une suite de rapports traite les accès toutes les heures. En factorisant le temps de traitement nécessaire de 30 minutes maximum, il peut s’écouler jusque 90 minutes avant que l’accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur de Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* **Attente du service push**

   Le service push (APNS ou GCM) n’envoie pas toujours immédiatement le message. Bien qu’inhabituel, il arrive que les délais d’attente soient de 5 à 10 minutes. Vous pouvez vérifier que le message push est envoyé vers le service push en regardant l’affichage **[!UICONTROL Rapport]** du message push, en trouvant le message dans le tableau **[!UICONTROL Historique du message]et en regardant le nombre de** Publié&#x200B;**.**

   >[!TIP]
   >
   >Ce nombre correspond au nombre d'envois réussis au ou aux services Push. Les services push ne garantissent pas qu’un message sera envoyé.

   Pour plus d'informations sur la fiabilité du service, voir :

   * [Qualité du service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Durée de vie d'un message](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Pourquoi ma clé d’API GCM Android est-elle incorrecte ?

* **Clé API non valide**

   Votre clé API peut être invalide pour les raisons suivantes :

   * La clé API que vous avez saisie n’est pas une clé de serveur correspondant à la valeur API GCM correcte.
   * La clé de serveur a mis les IP sur liste blanche et empêche les serveurs Adobe d’envoyer un message push.

* **Détermination de la validité d’une clé API**

   Pour déterminer la validité de la clé d’API, exécutez la commande suivante :

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Si le code d’état HTTP 401 est renvoyé, votre clé d’API est invalide. Sinon, le code ressemble à ce qui suit :

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## Pourquoi mon certificat APNS ne fonctionne-t-il pas ?

Votre certificat APNS peut être invalide pour les raisons suivantes :

* Vous pouvez utiliser un certificat de test Sandbox plutôt qu’un certificat de production.
* Vous utilisez un nouveau certificat de production/test Sandbox qui n’est pas pris en charge.
* You are using `.p8` file instead of a `.p12` file.

## Résolution des dysfonctionnements des messages push

**Un exemple**

L’exemple suivant présente comment résoudre un dysfonctionnement des messages push lors de l’utilisation d’une suite de rapports virtuelle.

Le client suivant possède deux applications iOS :

* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * VRSID : PhotoShop_iOS_app_SF
   * Segment de définition de VRSID : `a.appid contains “PhotoShop_iOS_app_SF”`
* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * RSID : Photoshop_ ios_ app_ LA
   * Segment de définition de VRSID : `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. Si toutes les applications **ne possèdent pas** de certificat valide, vos segments d’audience pourront être placés définitivement sur liste noire, et vous pourrez ne plus être en mesure de leur envoyer des messages push ultérieurement. Pour plus d'informations sur les segments d'audience, voir [Audience : définissez et configurez les options d'audience pour les messages Push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

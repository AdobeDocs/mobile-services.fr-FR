---
description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
keywords: mobile
seo-description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
seo-title: Résolution des problèmes liés aux messages push
solution: Experience Cloud,Analytics
title: Résolution des problèmes liés aux messages push
topic: Mesures
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Dépannage de la messagerie push{#troubleshooting-push-messaging}

Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* **Attente des accès Analytics**

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. Par défaut, ce traitement a lieu toutes les heures.

   Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. À titre d’exemple, une suite de rapports traite les accès toutes les heures. En factorisant le temps de traitement nécessaire de 30 minutes maximum, il peut s’écouler jusque 90 minutes avant que l’accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur de Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* **Attente du service push**

   Le service push (APNS ou GCM) n’envoie pas toujours immédiatement le message. Bien qu’inhabituel, il arrive que les délais d’attente soient de 5 à 10 minutes. Vous pouvez vérifier que le message push est envoyé vers le service push en regardant l’affichage **[!UICONTROL Rapport]** du message push, en trouvant le message dans le tableau **[!UICONTROL Historique du message]** et en regardant le nombre de **[!UICONTROL Publié]**.

   >[!TIP]
   >
   >Ce nombre correspond au nombre d’envois réussis vers le ou les services push. Les services push ne garantissent pas qu’un message sera envoyé.

   Pour plus d’informations sur la fiabilité du service, voir :

   * [Qualité de service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Durée de vie d’un message](https://developers.google.com/cloud-messaging/concept-options#lifetime).

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

   Vous pouvez également vérifier la validité d’un jeton d’enregistrement en remplaçant `"ABC"` par le jeton.

## Pourquoi mon certificat APNS ne fonctionne-t-il pas ?

Votre certificat APNS peut être invalide pour les raisons suivantes :

* Vous pouvez utiliser un certificat de test Sandbox plutôt qu’un certificat de production.
* Vous utilisez un nouveau certificat de production/test Sandbox qui n’est pas pris en charge.
* Vous utilisez un fichier `.p8` au lieu d’un fichier `.p12`.

## Résolution des dysfonctionnements des messages push

**Un exemple**

L’exemple suivant présente comment résoudre un dysfonctionnement des messages push lors de l’utilisation d’une suite de rapports virtuelle.

Le client suivant possède deux applications iOS :

* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * VRSID : PhotoShop_iOS_app_SF
   * Segment de définition VRSID : `a.appid contains “PhotoShop_iOS_app_SF”`
* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * RSID : PhotoShop_iOS_app_LA
   * Segment de définition VRSID : `a.os contains “iOS”`

Dans cet exemple, si un employé Photoshop envoie un message push à l’application *PhotoShop_iOS_app_SF*, tous les *utilisateurs de l’application PhotoShop_iOS_app_SF* recevront le message push, comme attendu. Mais si l’employé envoie un message à l’application *PhotoShop_iOS_app_LA*, car son segment de définition VRSID est incorrect (`iOS` au lieu de `a.os contains "PhotoShop_iOS_app_LA"`), le message est envoyé à **tous** les utilisateurs iOS dans *AllAdobe PhotoShop_apps*. Bien que le message soit toujours adressé aux utilisateurs de *PhotoShop_iOS_app_LA*, il met également sur liste noire les ID push pour les utilisateurs de *PhotoShop_iOS_app_SF* car l’application *PhotoShop_iOS_app_SF* a un certificat différent. Si le segment avait été défini comme `a.os contains “PhotoShop_iOS_app_LA”`, le message push aurait été envoyé uniquement aux utilisateurs de l’application *PhotoShop_iOS_app_LA*.

Si le message est envoyé avec le certificat push de l’application *PhotoShop_IOS_app_LA*, les identifiants push pour *PhotoShop_iOS_app_SF* reviendront comme `invalid`.

>[!CAUTION]
>
>Après avoir créé un message push pour une application qui utilise une suite de rapports virtuelle et cliqué sur **[!UICONTROL Enregistrer et envoyer]**, une alerte s’affiche pour vous rappeler que chaque application listée **doit** disposer d’un certificat valide. Si toutes les applications **ne possèdent pas** de certificat valide, vos segments d’audience pourront être placés définitivement sur liste noire, et vous pourrez ne plus être en mesure de leur envoyer des messages push ultérieurement. Pour plus d’informations sur les segments d’audience, voir [Audience : Définition et configuration des options d’audience pour les messages push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

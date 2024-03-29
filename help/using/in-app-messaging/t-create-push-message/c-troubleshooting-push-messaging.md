---
description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Résolution des problèmes liés aux messages push
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 100%

---

# Résolution des problèmes liés aux messages push{#troubleshooting-push-messaging}

{#eol}

Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* **Attente des accès Analytics**

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. Par défaut, ce traitement a lieu toutes les heures.

   Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. À titre d’exemple, une suite de rapports traite les correspondances toutes les heures. En tenant compte du temps de traitement requis de 30 minutes au maximum, il peut s’écouler jusqu’à 90 minutes avant qu’un accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur d’Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* **Attente du service push**

   Le service push (APNS ou GCM) n’envoie pas toujours le message immédiatement. Bien qu’inhabituel, il arrive que les délais d’attente soient de 5 à 10 minutes. Vous pouvez vérifier que le message push est envoyé vers le service push en regardant l’affichage **[!UICONTROL Rapport]** du message push, en trouvant le message dans le tableau **[!UICONTROL Historique du message]** et en regardant le nombre de **[!UICONTROL Publié]**.

   >[!TIP]
   >
   >Les services push ne garantissent pas qu’un message sera envoyé. Pour obtenir plus d’informations sur la fiabilité des services, voir la documentation appropriée :
   >
   >* **APNS** : [Qualité du service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM** : [Durée de vie d’un message](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Pourquoi ma clé API GCM Android est-elle incorrecte ?

* **Clé API non valide**

   Votre clé API n’est peut-être pas valide pour les raisons suivantes :

   * La clé que vous avez fournie n’est pas une clé de serveur avec la valeur de clé API GCM correcte.
   * La clé de serveur a autorisé les adresses IP et empêche les serveurs Adobe d’envoyer un message push.

* **Vérification de la validité de la clé API**

   Pour vérifier la validité de la clé d’API, exécutez la commande suivante :

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Si le code d’état HTTP 401 est renvoyé, votre clé API est incorrecte. Sinon, le code ressemble à ce qui suit :

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Vous pouvez également vérifier la validité d’un jeton d’enregistrement en remplaçant `"ABC"` par le jeton.

## Pourquoi mon certificat APNS ne fonctionne-t-il pas ?

Votre certificat APNS n’est peut-être pas valide pour les raisons suivantes :

* Il est possible que vous utilisiez un certificat de sandbox au lieu du certificat de production.
* Vous utilisez un nouveau certificat de production ou de sandbox qui n’est pas pris en charge.
* Vous utilisez un fichier `.p8` au lieu d’un fichier `.p12`.

## Résolution des dysfonctionnements des messages push

L’exemple suivant explique comment résoudre un échec de message push lors de l’utilisation d’une suite de rapports virtuelle.

Le client suivant possède deux applications iOS :

* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * VRSID : PhotoShop_iOS_app_SF
   * Segment de définition VRSID : `a.appid contains "PhotoShop_iOS_app_SF"`
* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * RSID : PhotoShop_iOS_app_LA
   * Segment de définition VRSID : `a.os contains "iOS"`

Dans cet exemple, si un employé Photoshop envoie un message push à l’application *PhotoShop_iOS_app_SF*, tous les *utilisateurs de l’application PhotoShop_iOS_app_SF* recevront le message push, comme attendu. Mais si l’employé envoie un message à l’application *PhotoShop_iOS_app_LA*, car son segment de définition VRSID est incorrect (`iOS` au lieu de `a.os contains "PhotoShop_iOS_app_LA"`), le message est envoyé à **tous** les utilisateurs iOS dans *AllAdobe PhotoShop_apps*. Bien que le message soit toujours adressé aux utilisateurs de *PhotoShop_iOS_app_LA*, il met également sur liste de blocage les ID push pour les utilisateurs de *PhotoShop_iOS_app_SF* car l’application *PhotoShop_iOS_app_SF* a un certificat différent. Si le segment avait été défini comme `a.os contains "PhotoShop_iOS_app_LA"`, le message push aurait été envoyé uniquement aux utilisateurs de l’application *PhotoShop_iOS_app_LA*.

Si le message est envoyé avec le certificat push de l’application *PhotoShop_IOS_app_LA*, les identifiants push pour *PhotoShop_iOS_app_SF* reviendront comme `invalid`.

>[!CAUTION]
>
>Après avoir créé un message push pour une application qui utilise une suite de rapports virtuelle et cliqué sur **[!UICONTROL Enregistrer et envoyer]**, une alerte s’affiche pour vous rappeler que chaque application listée **doit** disposer d’un certificat valide. Si toutes les applications **ne possèdent pas** de certificat valide, vos segments d’audience pourront être placés définitivement sur liste de blocage, et vous pourrez ne plus être en mesure de leur envoyer des messages push ultérieurement. Pour plus d’informations sur les segments d’audience, voir [Audience : Définition et configuration des options d’audience pour les messages push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

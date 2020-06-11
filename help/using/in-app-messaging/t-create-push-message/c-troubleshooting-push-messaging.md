---
description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
keywords: mobile
seo-description: Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.
seo-title: Résolution des problèmes liés aux messages push
solution: Marketing Cloud,Analytics
title: Résolution des problèmes liés aux messages push
topic: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 59%

---


# Dépannage de la messagerie push{#troubleshooting-push-messaging}

Ces informations peuvent vous aider à résoudre les problèmes liés aux messages push.

## Pourquoi l’envoi des messages push est-il parfois retardé ?

Les types suivants de retards peuvent être associés aux messages push pour Mobile Services :

* **Attente des accès Analytics**

   Chaque suite de rapports comporte un paramètre permettant de déterminer le moment du traitement des accès Analytics entrants. Par défaut, ce traitement a lieu toutes les heures.

   Le traitement effectif des accès Analytics peut prendre jusqu’à 30 minutes, mais il est normalement de 15 à 20 minutes. Par exemple, une suite de rapports traite les accès toutes les heures. Lorsque vous prenez en compte le temps de traitement requis de 30 minutes au maximum, il peut s’écouler jusqu’à 90 minutes avant qu’un accès entrant soit disponible pour un message push. Si un utilisateur a lancé l’application à 9 h 01, l’accès se présente dans l’interface utilisateur de Adobe Mobile Services en tant que nouvel utilisateur unique entre 10 h 15 et 10 h 30.

* **En attente du service Push**

   Le service Push (APNS ou GCM) n’envoie pas immédiatement le message. Bien qu’inhabituel, il arrive que les délais d’attente soient de 5 à 10 minutes. Vous pouvez vérifier que le message push est envoyé vers le service push en regardant l’affichage **[!UICONTROL Rapport]** du message push, en trouvant le message dans le tableau **[!UICONTROL Historique du message]** et en regardant le nombre de **[!UICONTROL Publié]**.

   >[!TIP]
   >
   >Ce nombre correspond au nombre d’envois réussis vers le ou les services push. Les services push ne garantissent pas qu’un message sera envoyé.

   Pour plus d’informations sur la fiabilité du service, voir :

   * [Qualité de service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Durée de vie d’un message](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Pourquoi ma clé d’API GCM Android est-elle non valide ?

* **Clé d&#39;API non valide**

   Votre clé d&#39;API n&#39;est peut-être pas valide pour les raisons suivantes :

   * La clé d’API que vous avez fournie n’est pas une clé de serveur avec la valeur de clé d’API GCM correcte.
   * La clé de serveur a autorisé les adresses IP et empêche les serveurs Adobe d&#39;envoyer un message push.

* **Déterminer la validité de la clé d&#39;API**

   Pour déterminer la validité de votre clé d&#39;API, exécutez la commande suivante :

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Un code d&#39;état HTTP 401 renvoyé signifie que votre clé d&#39;API n&#39;est pas valide. Sinon, vous verrez quelque chose de similaire :

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Vous pouvez également vérifier la validité d’un jeton d’enregistrement en remplaçant `"ABC"` par le jeton.

## Pourquoi mon certificat APNS ne fonctionne-t-il pas ?

Votre certificat APNS peut être non valide pour les raisons suivantes :

* Vous pouvez utiliser un certificat sandbox au lieu du certificat de production.
* Vous utilisez un nouveau certificat de production/sandbox qui n’est pas pris en charge.
* Vous utilisez un fichier `.p8` au lieu d’un fichier `.p12`.

## Résolution des dysfonctionnements des messages push

**Un exemple**

L’exemple suivant illustre comment résoudre un échec de type Push lors de l’utilisation d’une suite de rapports virtuelle.

Le client suivant possède deux applications iOS :

* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * VRSID : PhotoShop_iOS_app_SF
   * Segment de définition VRSID : `a.appid contains “PhotoShop_iOS_app_SF”`
* Nom de l’application : PhotoShop_app_iOS
   * RSID parent : AllAdobe PhotoShop_apps
   * RSID : PhotoShop_iOS_app_LA
   * Segment de définition VRSID : `a.os contains “iOS”`

Dans cet exemple, si un employé Photoshop envoie un message push à l’application *PhotoShop_iOS_app_SF*, tous les *utilisateurs de l’application PhotoShop_iOS_app_SF* recevront le message push, comme attendu. Mais si l’employé envoie un message à l’application *PhotoShop_iOS_app_LA*, car son segment de définition VRSID est incorrect (`iOS` au lieu de `a.os contains "PhotoShop_iOS_app_LA"`), le message est envoyé à **tous** les utilisateurs iOS dans *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blocklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. Si le segment avait été défini comme `a.os contains “PhotoShop_iOS_app_LA”`, le message push aurait été envoyé uniquement aux utilisateurs de l’application *PhotoShop_iOS_app_LA*.

Si le message est envoyé avec le certificat push de l’application *PhotoShop_IOS_app_LA*, les identifiants push pour *PhotoShop_iOS_app_SF* reviendront comme `invalid`.

>[!CAUTION]
>
>Après avoir créé un message push pour une application qui utilise une suite de rapports virtuelle et cliqué sur **[!UICONTROL Enregistrer et envoyer]**, une alerte s’affiche pour vous rappeler que chaque application listée **doit** disposer d’un certificat valide. If each app does **not** have a valid certificate, your audience segments might be indefinitely blocklisted, and you might not be able to send future push messages to the affected users. Pour plus d’informations sur les segments d’audience, voir [Audience : Définition et configuration des options d’audience pour les messages push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

---
description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.
seo-description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.
seo-title: Messagerie Push
solution: Experience Cloud,Analytics
title: Messagerie Push
topic: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '439'
ht-degree: 100%

---


# Messagerie Push {#push-messaging}

Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de créer rapidement des rapports sur les utilisateurs qui ont ouvert votre application suite à un clic sur le message push.

Pour utiliser les messages push, vous **devez** disposer du SDK version 4.6 ou supérieure.

>[!IMPORTANT]
>
>Ne définissez pas manuellement l’Experience Cloud ID dans l’application. Ceci provoque la création d’un nouvel utilisateur unique qui ne recevra pas de messages push en raison de son état d’inclusion. Par exemple, un utilisateur qui s’est abonné pour recevoir des messages push se connecte à votre application. Une fois connecté, si vous définissez manuellement l’identifiant dans votre application, un nouvel utilisateur unique est créé qui n’a pas choisi de recevoir de messages push. Ce nouvel utilisateur ne recevra pas vos messages Push.
>
>Vous ne pouvez pas déplacer votre application vers une nouvelle suite de rapports. Si vous migrez vers une nouvelle suite de rapports, votre configuration push peut devenir défaillante et les messages peuvent ne pas être envoyés.

## Activation de la messagerie push {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Si votre application est déjà configurée pour utiliser la messagerie par l’intermédiaire de Firebase Cloud Messaging (FCM), certaines étapes sont peut-être déjà terminées.

1. Vérifiez que le fichier `ADBMobileConfig.json` contient les paramètres requis pour la messagerie push.

   La propriété `"marketingCloud"` de l’objet `"org"` doit être configurée pour la messagerie push.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Obtenez le jeton/ID d’enregistrement à l’aide de l’API Firebase Cloud Messaging (FCM).

   * Pour obtenir plus d’informations sur la configuration FCM, voir [Configuration d’une application cliente FCM sous Android](https://firebase.google.com/docs/cloud-messaging/android/client).

   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. L’identifiant/le jeton d’enregistrement doit être transmis au SDK à l’aide de la méthode `Config.setPushIdentifier(final String registrationId)`.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Activez la création de rapports en transmettant votre activité dans la méthode `collectLifecycleData`.

   Vous trouverez ci-dessous les exigences relatives à l’activation de la création de rapports sur les clics publicitaires Push :

   * Dans la mise en œuvre de `FireBaseMessageService`, l’objet Bundle qui comporte les données de message, qui sont transmises à la méthode `onMessageReceived` avec l’objet RemoteMessage, doit être ajouté à l’intention qui est utilisée pour ouvrir l’activité cible lors d’un clic publicitaire. Vous pouvez le faire à l’aide de la `putExtras` méthode. Pour en savoir plus, consultez la rubrique [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle)).

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Dans l’activité cible du clic publicitaire, l’activité doit être transmise au SDK avec l’appel `collectLifecycleData`.

      À noter :

      * Utilisez `Config.collectLifecycleData(this)` ou `Config.collectLifecycleData(this, contextData)`.

      * **N’utilisez pas** `Config.collectLifecycleData()`.




---
description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de repérer facilement les utilisateurs qui ont ouvert votre application après avoir cliqué sur un message Push.
seo-description: Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de repérer facilement les utilisateurs qui ont ouvert votre application après avoir cliqué sur un message Push.
seo-title: Messagerie Push
solution: Marketing Cloud,Analytics
title: Messagerie Push
topic: Développeur et mise en œuvre
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile et le SDK Adobe Mobile permettent d’envoyer des messages Push aux utilisateurs. Le SDK permet également de repérer facilement les utilisateurs qui ont ouvert votre application après avoir cliqué sur un message Push.

Pour utiliser la messagerie Push, vous **devez** disposer du SDK version 4.6 ou supérieure.

>[!IMPORTANT]
>
>Ne définissez pas manuellement l’ID Experience Cloud dans votre application. Cela provoque la création d’un nouvel utilisateur unique qui ne recevra pas les messages Push en raison de son état d’inclusion. Par exemple, un utilisateur qui a choisi de recevoir des messages push se connecte à votre application. Après la connexion, si vous définissez manuellement l’identifiant dans l’application, un nouvel utilisateur unique est créé qui n’a pas choisi de recevoir les messages push. Ce nouvel utilisateur ne recevra pas vos messages Push.
>
>Le déplacement de votre application vers une nouvelle suite de rapports n’est pas pris en charge. Si vous migrez vers une nouvelle suite de rapports, votre configuration push peut devenir défaillante et les messages peuvent ne pas être envoyés.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Si votre application est déjà configurée pour utiliser la messagerie via Firebase Cloud Messaging (FCM), certaines des étapes suivantes peuvent déjà être effectuées.

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

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

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Activez la création de rapports en transmettant votre activité dans la méthode `collectLifecycleData`.

   Vous trouverez ci-dessous les exigences relatives à l’activation de la création de rapports sur les clics publicitaires Push :

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. Vous pouvez le faire à l’aide de la `putExtras` méthode. For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Dans l’activité cible du clic publicitaire, l’activité doit être transmise au SDK avec l’appel `collectLifecycleData`.

      À noter :

      * Utilisez `Config.collectLifecycleData(this)` ou `Config.collectLifecycleData(this, contextData)`.

      * Do **not** use `Config.collectLifecycleData()`.




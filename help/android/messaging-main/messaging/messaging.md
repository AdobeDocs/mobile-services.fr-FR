---
description: Vous pouvez envoyer des messages in-app déclenchés par une donnée ou un événement Analytics. Après la mise en œuvre, les messages sont envoyés dynamiquement à l’application et ne requièrent pas de mise à jour du code.
seo-description: Vous pouvez envoyer des messages in-app déclenchés par une donnée ou un événement Analytics. Après la mise en œuvre, les messages sont envoyés dynamiquement à l’application et ne requièrent pas de mise à jour du code.
seo-title: Messagerie in-app
solution: Marketing Cloud, Analytics
title: Messagerie in-app
topic: Développeur et mise en œuvre
uuid: 351 ee 3 d 2-80 b 9-4 f 2 d -9696-21 f 274 d 89 f 5 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-app messaging {#in-app-messaging}

Vous pouvez envoyer des messages in-app déclenchés par une donnée ou un événement Analytics. Après la mise en œuvre, les messages sont envoyés dynamiquement à l’application et ne requièrent pas de mise à jour du code.

## Nouvelle mise à jour du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation à propos du SDK Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter notre documentation la plus récente.

>[!IMPORTANT]
>
>Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Pour commencer, cliquez sur [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Pour utiliser la messagerie in-app, vous **devez** disposer du SDK version 4.2 ou supérieure.

Vous pouvez créer des messages et les règles dans Adobe Mobile Services qui définissent le moment où les messages s’affichent. Pour obtenir plus d’informations, voir [Création d’un message in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Pour afficher des messages in-app, des mises à jour doivent être apportées au SDK. Vous pouvez terminer ces étapes même si vous n’avez pas encore défini de messages. Une fois que vous avez défini les messages, ils sont envoyés dynamiquement à l’application et affichés sans mise à jour de la boutique d’applications.

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier Config à votre projet intellij IDEA ou Eclipse* dans [l'implémentation principale et le cycle de vie](/help/android/getting-started/dev-qs.md).

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Si vous avez sélectionné une disposition modale, sélectionnez un des thèmes suivants pour le message :

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   Par exemple :

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Dans chaque appel `collectLifecycleData`, transmettez `this` pour fournir une référence à l’activité en cours :

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` ou est `remotes` obligatoire.

   Pour que les messages in-app soient mis à jour dynamiquement au lancement, l’objet `remotes` doit être présent et correctement configuré :

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Pour obtenir plus d’informations, voir [Avant de commencer](/help/android/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Les SDK Android Mobile Services effectuent le suivi des mesures suivantes pour vos messages in-app :

* Pour les messages in-app en plein écran et de type alerte :

   * **Impressions** : lorsque l’utilisateur déclenche un message in-app.
   * **Clics publicitaires**: lorsque l'utilisateur clique **[!UICONTROL sur Clic publicitaire]**.
   * **Annuels**: lorsque l'utilisateur appuie **[!UICONTROL sur Annuler]**.

* Pour les messages in-app personnalisés en plein écran, le contenu HTML du message doit contenir le code approprié pour notifier le suivi du SDK concernant les boutons suivants :

   * **Suivi des exemples de clics** publicitaires (redirection) :

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Annuler** (fermer) l'exemple de suivi :

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Lors de la création d’un message Plein écran, vous avez la possibilité, si vous le souhaitez, de spécifier une image de secours. Si le message ne peut pas récupérer l’image prévue depuis le web, le SDK tente de charger l’image portant le même nom depuis le dossier assets de l’application. Cela permet d’afficher le message dans son format d’origine, même si l’utilisateur est hors ligne ou si l’image prédéterminée n’est pas accessible.

>[!IMPORTANT]
>
>Le nom du fichier d'image de secours est spécifié lorsque vous configurez le message dans les services Adobe Mobile et vous devez vous assurer que la ressource indiquée est disponible.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Les méthodes suivantes permettent de configurer la petite icône et la grande icône qui apparaissent dans la zone de notification ainsi que la grande icône affichée lorsque des notifications apparaissent dans le tiroir de notification.

* **Config.setSmallIconResourceId(int resourceId)**

   Définit la petite icône qui sera utilisée pour les notifications créées par le SDK. Cette icône apparaît dans la barre d’état et est l’image secondaire qui s’affiche lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notifications.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Voici l'exemple de code pour cette méthode :

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Définit la grande icône qui sera utilisée pour les notifications créées par le SDK. Cette icône est l'image principale affichée lorsque l'utilisateur voit la notification complète dans le centre de notification.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```

---
description: Vous pouvez diffuser des messages in-app qui sont déclenchés à partir de n’importe quelle donnée ou événement d’analyse. Après la mise en œuvre, les messages sont dynamiquement diffusés dans l’application et ne nécessitent pas de mise à jour du code.
seo-description: Vous pouvez diffuser des messages in-app qui sont déclenchés à partir de n’importe quelle donnée ou événement d’analyse. Après la mise en œuvre, les messages sont dynamiquement diffusés dans l’application et ne nécessitent pas de mise à jour du code.
seo-title: Messagerie in-app
solution: Experience Cloud,Analytics
title: Messagerie in-app
topic: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---


# Messagerie in-app {#in-app-messaging}

Vous pouvez diffuser des messages in-app qui sont déclenchés à partir de n’importe quelle donnée ou événement d’analyse. Après la mise en œuvre, les messages sont dynamiquement diffusés dans l’application et ne nécessitent pas de mise à jour du code.

## Nouvelle version du SDK Adobe Experience Cloud

Vous recherchez des informations et de la documentation concernant le SDK d’Adobe Experience Platform Mobile ? Cliquez [ici](https://aep-sdks.gitbook.io/docs/) pour consulter la documentation la plus récente.

>[!IMPORTANT]
>
>Nous avons lancé, en septembre 2018, une version majeure du SDK. Ces nouveaux SDK Adobe Experience Platform Mobile peuvent être configurés via [Experience Platform Launch](https://www.adobe.com/fr/experience-platform/launch.html).

* Pour commencer, accédez à [Launch](https://launch.adobe.com/).
* Pour consulter le contenu des dépôts du SDK Experience Platform, accédez à [Github : Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Si vous utilisez les SDK Adobe Experience Platform Mobile avec Adobe Launch, vous **devez** également installer l’extension Adobe Analytics Mobile Services pour utiliser les fonctionnalités Adobe Mobile Services comme la messagerie intégrée (in-app) et les notifications Push. Pour en savoir plus, reportez-vous à la section [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Pour plus d’informations sur l’utilisation de la messagerie push et de la messagerie in-app avec les SDK Experience Cloud, voir [Configuration de la messagerie push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) et [Configuration de la messagerie in-app](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Pour utiliser la messagerie in-app, vous **devez** disposer du SDK version 4.2 ou supérieure.

Vous pouvez créer des messages et des règles dans Adobe Mobile Services qui définissent le moment où les messages s’affichent. Pour plus d’informations, voir [Créer un message in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Pour afficher les messages in-app, des mises à jour doivent être apportées au SDK. Vous pouvez suivre ces étapes même si vous n’avez encore défini aucun message. Une fois que vous avez défini les messages, ils sont envoyés dynamiquement à l’application et affichés sans mise à jour de la boutique d’applications.

## Activation de la messagerie in-app {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration au projet IntelliJ IDEA ou Eclipse* dans [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

1. Mettez à jour le fichier `AndroidManifest.xml` pour déclarer l’activité Plein écran et activer le gestionnaire de notifications de messages :

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

1. Vérifiez que le fichier `ADBMobileConfig.json` contient les paramètres requis pour la messagerie intégrée (in-app).

   >[!IMPORTANT]
   >
   >`messages` ou `remotes` est obligatoire.

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

   Si cet objet n’est pas configuré, téléchargez un fichier `ADBMobileConfig.json` mis à jour depuis Adobe Mobile Services. Pour obtenir plus d’informations, voir [Avant de commencer](/help/android/getting-started/requirements.md).

## Suivi des messages in-app {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Les SDK Android Mobile effectuent le suivi des mesures suivantes pour vos messages in-app :

* Pour les messages in-app en mode plein écran et de style alerte :

   * **Impressions** : lorsque l’utilisateur déclenche un message in-app.
   * **Clics publicitaires** : lorsque l’utilisateur appuie sur **[!UICONTROL Clic publicitaire]**.
   * **Annulations** : lorsque l’utilisateur appuie sur **[!UICONTROL Annuler]**.

* Pour les messages in-app personnalisés en plein écran, le contenu HTML du message doit contenir le code approprié pour notifier le suivi du SDK concernant les boutons suivants :

   * Exemple de suivi des **Clics publicitaires** (redirections) :

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * Exemple de suivi - **Annuler** (fermer) :

      `adbinapp://cancel`

## Image de secours locale {#section_DEACC1CE549B4573B556A44A52409941}

Lors de la création d’un message en plein écran, vous pouvez éventuellement spécifier une image de secours. Si votre message ne parvient pas à récupérer l’image qui lui est destinée sur le Web, le SDK tente de charger l’image portant le même nom depuis le dossier assets de votre application. Vous pouvez ainsi afficher votre message sous sa forme d’origine, même si l’utilisateur est hors ligne ou si l’image prédéterminée est inatteignable.

>[!IMPORTANT]
>
>Le nom de ressource de l’image de secours est spécifié lors de la configuration du message dans Adobe Mobile Services. Vous devez vous assurer que la ressource spécifiée est disponible.

## Configuration des icônes de notification {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Les méthodes suivantes permettent de configurer la petite icône et la grande icône qui apparaissent dans la zone de notification ainsi que la grande icône affichée lorsque des notifications apparaissent dans le tiroir de notification.

* **Config.setSmallIconResourceId(int resourceId)**

   Définit la petite icône qui sera utilisée pour les notifications créées par le SDK. Cette icône apparaît dans la barre d’état et est l’image secondaire qui s’affiche lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notification.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Voici un exemple de code pour cette méthode :

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Définit la grande icône qui sera utilisée pour les notifications créées par le SDK. Cette icône est l’image principale affichée lorsque l’utilisateur voit l’ensemble de la notification dans le Centre de notifications.

   * Voici la syntaxe de cette méthode :

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Voici l’exemple de code pour cette méthode :

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```

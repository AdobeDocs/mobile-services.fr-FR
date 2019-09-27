---
description: Ces informations vous aideront à mettre en œuvre la bibliothèque Android et à collecter les mesures de cycle de vie, par exemple les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.
keywords: android;library;mobile;sdk
seo-description: Ces informations vous aideront à mettre en œuvre la bibliothèque Android et à collecter les mesures de cycle de vie, par exemple les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.
seo-title: Mise en œuvre principale et cycle de vie
solution: Marketing Cloud,Analytics
title: Mise en œuvre principale et cycle de vie
topic: Développeur et mise en œuvre
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbb2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Ces informations vous aideront à mettre en œuvre la bibliothèque Android et à collecter les mesures de cycle de vie, par exemple les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc.

## Téléchargement du kit SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDK, you must use Android 2.2 or later.

1. Suivez les procédures décrites dans les sections ci-après pour configurer une suite de rapports de développement et télécharger une version prérenseignée du fichier de configuration :

   * [Création d’une suite de rapports](/help/android/getting-started/requirements.md)
   * [Téléchargement du SDK](/help/android/getting-started/requirements.md)

1. Téléchargez et décompressez le `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` fichier et vérifiez que les composants logiciels suivants existent :

   * `adobeMobileLibrary.jar`, qui est la bibliothèque qui sera utilisée avec les appareils et simulateurs Android.

   * `ADBMobileConfig.json` : fichier de configuration du SDK personnalisé pour votre application.
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**Projet IntelliJ IDEA**

Pour ajouter le SDK et le fichier de configuration au projet, procédez comme suit :

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. Cliquez avec le bouton droit sur le projet dans le volet de navigation du projet.
1. Sélectionnez **[!UICONTROL Ouvrir les paramètres du module]**.
1. Sous **[!UICONTROL Paramètres du projet]**, sélectionnez **[!UICONTROL Bibliothèques]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. Sélectionnez **[!UICONTROL Java]** et accédez au fichier `adobeMobileLibrary.jar`.
1. Sélectionnez les modules dans lesquels vous prévoyez d’utiliser la bibliothèque mobile.
1. Cliquez sur **[!UICONTROL Appliquer]**, puis sur **[!UICONTROL OK]pour fermer la fenêtre Paramètres du module.**

**Projet Eclipse**

Pour ajouter le SDK et le fichier de configuration au projet, procédez comme suit :

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. In **[!UICONTROL Eclipse IDE]**, right-click the project name.
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. Select `adobeMobileLibrary.jar`.
1. Cliquez sur **[!UICONTROL Ouvrir]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. Dans l’onglet **[!UICONTROL Ordonner et exporter]**, assurez-vous que le fichier **`adobeMobileLibrary.jar`est sélectionné.**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

La bibliothèque AppMeasurement nécessite les autorisations suivantes pour envoyer des données et enregistrer les appels de suivi hors ligne :

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Pour ajouter ces autorisations, ajoutez les lignes suivantes au fichier `AndroidManifest.xml` situé dans le répertoire du projet d’application :

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

Le code suivant doit être ajouté à la `onCreate` méthode de votre activité principale :

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

Une fois que vous avez activé le cycle de vie, chaque fois que l’application est lancée, un accès est envoyé permettant de mesurer les lancements, les mises à niveau, les sessions, les utilisateurs actifs, etc. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

**Procédez comme suit pour chaque activité de votre application :**

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Pour la fonction `onResume`, démarrez la collecte des données du cycle de vie :

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. Pour la fonction `onPause`, arrêtez la collecte des données du cycle de vie :

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>Vous devez ajouter ces appels à chaque activité pour garantir la précision des rapports de plantage. Pour plus d’informations, voir [Suivi des blocages](/help/android/analytics-main/crashes.md)d’application.

## Inclure des données supplémentaires avec les appels de cycle de vie

Pour inclure des données supplémentaires aux appels de mesures de cycle de vie, transmettez un paramètre supplémentaire à `collectLifecycleData` qui contient les données contextuelles :

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

Les valeurs des données contextuelles supplémentaires envoyées avec `collectLifecycleData` doivent être mises en correspondance avec les variables personnalisées dans Adobe Mobile Services :

![](assets/map-variable-lifecycle.png)

Les autres mesures de cycle de vie sont collectées automatiquement. Pour en savoir plus, voir la section [Mesures de cycle de vie](/help/android/metrics.md).

## Étapes suivantes {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Exécutez les tâches ci-après :

* [Suivi des états de l’application](/help/android/analytics-main/states.md)
* [Suivi des actions de l’application](/help/android/analytics-main/actions.md)


---
description: À compter de la version 4.5 du SDK Android, une nouvelle extension Android a été ajoutée pour permettre la collecte des données à partir de l’application Android Wearable.
solution: Experience Cloud Services,Analytics
title: 'Android Wearables : Prise en main'
topic-fix: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
exl-id: 79cfaa48-d9b2-4518-8b31-d7041898a71b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 100%

---

# Android Wearables : Prise en main {#android-wearables-getting-started}

À compter de la version 4.5 du SDK Android, une nouvelle extension Android a été ajoutée pour permettre la collecte des données à partir de l’application Android Wearable.

## Configuration du SDK pour une application pour portables (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Pour plus d’informations sur l’importation du SDK dans votre projet, voir [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

1. Ajoutez le fichier `ADBMobileConfig.json` au dossier assets du projet.
1. Ajoutez le fichier `adobeMobileLibrary-*.jar` au dossier libs ou assurez-vous que ce fichier est référencé par le projet.

   >[!TIP]
   >
   >Vous devrez peut-être synchroniser le projet gradle après l’ajout du fichier `.jar`.

1. Pour la méthode `onCreate`, autorisez le SDK à accéder au contexte de l’application à l’aide de `Config.setContext` :

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Ajoutez le code suivant au `AndroidManifest.xml` fichier :

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Assurez-vous que votre projet comprend la bibliothèque des services Google Play.
1. Mettez en œuvre `WearableListenerService` ou ajoutez le code correspondant à `WearableListenerService` :

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. Ajouter `WearListenerService` au fichier `AndroidManifest.xml` :

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## Configuration du SDK pour une application pour wearables (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Procédez de l’une des manières suivantes :

   * Ajoutez le même fichier `ADBMobileConfig.json` au dossier assets de votre projet wearable.
   * Modifiez la configuration du projet gradle afin d’utiliser le fichier `ADBMobileConfig.json` dans le dossier assets de l’application pour portables :

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Ajoutez le fichier `adobeMobileLibrary-*.jar` au dossier libs ou assurez-vous qu’il est référencé par le projet.

   Vous devrez peut-être synchroniser le projet gradle après l’ajout du fichier jar.

1. Pour la méthode `onCreate`, permettez au SDK d’accéder au contexte de votre application en utilisant `Config.setContext` :

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. Ajoutez le code suivant à `AndroidManifest.xml` :

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Assurez-vous que votre projet comprend la bibliothèque de services de Google Play.
1. Mettez en œuvre `WearableListenerService` ou ajoutez le code correspondant à `WearableListenerService` :

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Ajouter `WearListenerService` au fichier `AndroidManifest.xml` :

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

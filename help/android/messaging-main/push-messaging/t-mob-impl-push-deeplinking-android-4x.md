---
description: Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé adb_deeplink.
title: Mise en oeuvre de la messagerie push avec la création de liens profonds
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# Mise en œuvre de la messagerie push avec la création de liens profonds {#implement-push-messaging-with-deep-linking}

Une fois l’URL de création de liens profonds configurée dans l’interface utilisateur Adobe Mobile Services, elle est incluse dans la charge utile Push avec la clé adb_deeplink.

Vous pouvez obtenir l’URL en appelant `remoteMessage.getData().get("adb_deeplink")` dans le `FirebaseMessagingService`.

>[!TIP]
>
>Vous pouvez définir différentes intentions selon que la charge utile comporte ou non une URL de création de liens profonds.

1. Procédez de l’une des manières suivantes :

   * Si l’URL de création de liens profonds **figure** dans la charge utile Push, créez une intention `ACTION_VIEW` avec l’URL.

      Lorsque l’utilisateur clique sur le message push, un lien profond est déclenché.

   * Si l’URL de création de liens profonds **n’est pas** dans la payload push, créez une intention qui ouvrira l’une de vos activités.

## Exemple

Voici un exemple de mise en œuvre pour la classe étendue à partir de `FirebaseMessagingService` :

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```

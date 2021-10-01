---
description: Vous pouvez joindre des fichiers image à vos notifications Android. L’ajout de composants visuels peut accroître considérablement l’engagement de votre utilisateur avec les notifications push.
title: Réception de notifications push enrichies
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
exl-id: 5776411c-aa0e-4e67-83aa-e78f5d1ed4f7
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 68%

---

# Réception de notifications push enrichies {#receive-rich-push-notifications}

Vous pouvez joindre des fichiers image à vos notifications Android. L’ajout de composants visuels peut accroître considérablement l’engagement de votre utilisateur avec les notifications push.

## Traitement du message Push enrichi entrant (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Si l’application est au premier plan, le message Push est traité par l’application qui étend la classe `FirebaseMessagingService`, puis il est déclaré dans le fichier de manifeste comme suit :

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>La classe qui contient la mise en œuvre `onMessageReceived()` traite les données reçues.

Si le message Push comporte une URL de média, l’URL est disponible dans le paramètre `RemoteMessage` qui est transmis à la fonction `onMessageReceived()`. La clé à utiliser est `attachment-url`, comme indiqué dans l’exemple de code suivant :

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>Si vous définissez `NotificationCompat.BigPictureStyle`, il se peut que les images de grande taille ne s’affichent pas. Pour assurer l’affichage des images de grande taille, définissez le paramètre natif `Notification.BigPictureStyle`.

## Exemple de notification Push enrichie {#section_6819316BEDDE45108413B541CA2BB2DC}

Voici un exemple de notification Push enrichie par une image :

![](assets/rich-push-notification_example.png)

Pour plus d’informations sur les notifications push enrichies avec Android, voir [Interagir avec les notifications enrichies](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).

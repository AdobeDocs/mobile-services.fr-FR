---
description: Vous pouvez joindre des fichiers image aux notifications Android. L’ajout de composants visuels peut sensiblement augmenter l’engagement de l’utilisateur avec des notifications Push.
seo-description: Vous pouvez joindre des fichiers image aux notifications Android. L’ajout de composants visuels peut sensiblement augmenter l’engagement de l’utilisateur avec des notifications Push.
seo-title: Réception de notifications Push enrichies
title: Réception de notifications Push enrichies
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

Vous pouvez joindre des fichiers image aux notifications Android. L’ajout de composants visuels peut sensiblement augmenter l’engagement de l’utilisateur avec des notifications Push.

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

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
>The class that contains the `onMessageReceived()` implementation handles the data that is received.

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. La clé à utiliser est `attachment-url`, comme indiqué dans l’exemple de code suivant :

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
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. Pour assurer l’affichage des images de grande taille, définissez le paramètre natif `Notification.BigPictureStyle`.

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

Voici un exemple de notification Push enrichie par une image :

![](assets/rich-push-notification_example.png)

Pour obtenir plus d’informations sur les notifications Push enrichies sous Android, voir [Stimuler l’intérêt des utilisateurs et élargir la visibilité de votre application grâce aux notifications](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).

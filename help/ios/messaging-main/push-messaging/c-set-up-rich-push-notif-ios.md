---
description: Vous pouvez joindre des fichiers image à vos notifications Apple. L’ajout d’éléments visuels peut augmenter de façon notable l’engagement de vos utilisateurs vis-à-vis des notifications push.
seo-description: Vous pouvez joindre des fichiers image à vos notifications Apple. L’ajout d’éléments visuels peut augmenter de façon notable l’engagement de vos utilisateurs vis-à-vis des notifications push.
seo-title: Réception de notifications push enrichies
title: Réception de notifications Push enrichies
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Vous pouvez joindre des fichiers image à vos notifications Apple. L’ajout d’éléments visuels peut augmenter de façon notable l’engagement de vos utilisateurs vis-à-vis des notifications push.

Pour recevoir des notifications push enrichies dans votre application iOS :

1. Mettez en œuvre la messagerie push pour l’application en suivant la procédure indiquée dans [Messagerie Push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Assurez-vous que vous pouvez envoyer un message texte push à votre application.
1. Ajoutez une extension de service de notification en suivant la procédure suivante :

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Sélectionnez **[!UICONTROL Extension de service de notification]**.
   1. Vérifiez que le fichier `NotificationService.m` existe.

1. Ouvrez le fichier `NotificationService.m` et vérifiez que les méthodes déléguées suivantes existent :

   * Une méthode destinée à recevoir la demande de notification.
   * Une méthode destinée à gérer l’expiration de l’extension de service.

      La première méthode est utilisée pour la réception de notifications push enrichies :

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      Dans cette méthode, vous pouvez obtenir l’URL du média à partir de `userInfo` la clé `attachment-url` . Après avoir téléchargé le fichier dans un répertoire local, ajoutez le chemin d’accès local à `bestAttemptContent.attachments`.

      Voici un exemple du code de cette méthode :

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


Pour obtenir plus d’informations sur l’utilisation de notifications push enrichies avec iOS, voir [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).

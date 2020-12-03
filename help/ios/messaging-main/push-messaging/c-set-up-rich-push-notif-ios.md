---
description: Vous pouvez joindre des fichiers image à vos notifications Apple. Ajouter des composants visuels peut augmenter considérablement l’engagement de vos utilisateurs avec les notifications Push.
seo-description: Vous pouvez joindre des fichiers image à vos notifications Apple. Ajouter des composants visuels peut augmenter considérablement l’engagement de vos utilisateurs avec les notifications Push.
seo-title: Recevoir des notifications Push enrichies
title: Recevoir des notifications Push enrichies
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 38%

---


# Réception de notifications push enrichies{#receive-rich-push-notifications}

Vous pouvez joindre des fichiers image à vos notifications Apple. Ajouter des composants visuels peut augmenter considérablement l’engagement de vos utilisateurs avec les notifications Push.

Pour recevoir des notifications Push riches dans votre application iOS :

1. Mettez en œuvre la messagerie push pour l’application en suivant la procédure indiquée dans [Messagerie Push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Vérifiez que vous pouvez envoyer un message Push texte à votre application.
1. Ajoutez une extension de service de notification en procédant comme suit :

   1. Dans le projet Xcode, sélectionnez **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. Sélectionnez **[!UICONTROL Extension de service de notification]**.
   1. Vérifiez que le fichier `NotificationService.m` existe.

1. Ouvrez le fichier `NotificationService.m` et vérifiez que les méthodes déléguées suivantes existent :

   * Une méthode pour recevoir une demande de notification.
   * Une méthode pour gérer l&#39;expiration de l&#39;extension de service.

      Pour recevoir des notifications Push enrichies, la première méthode est utilisée :

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      Dans cette méthode, vous pouvez obtenir l’URL du média à partir de `userInfo` en utilisant la clé `attachment-url`. Après avoir téléchargé le fichier dans un répertoire local, ajoutez le chemin d’accès local à `bestAttemptContent.attachments`.

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


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).

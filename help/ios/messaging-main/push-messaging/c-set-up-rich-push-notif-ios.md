---
description: Vous pouvez joindre des fichiers image à vos notifications Apple. L’ajout de composants visuels peut accroître considérablement l’engagement de vos utilisateurs avec les notifications push.
title: Réception de notifications push enrichies
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 43%

---

# Réception de notifications push enrichies {#receive-rich-push-notifications}

Vous pouvez joindre des fichiers image à vos notifications Apple. L’ajout de composants visuels peut accroître considérablement l’engagement de vos utilisateurs avec les notifications push.

Pour recevoir des notifications push enrichies dans votre application iOS :

1. Mettez en œuvre la messagerie push pour l’application en suivant la procédure indiquée dans [Messagerie Push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Vérifiez que vous pouvez envoyer un message push de texte à votre application.
1. Ajoutez une extension de service de notification en procédant comme suit :

   1. Dans le projet Xcode, sélectionnez **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. Sélectionnez **[!UICONTROL Extension de service de notification]**.
   1. Vérifiez que le fichier `NotificationService.m` existe.

1. Ouvrez le fichier `NotificationService.m` et vérifiez que les méthodes déléguées suivantes existent :

   * Une méthode pour recevoir une demande de notification.
   * Une méthode permettant de gérer l’expiration de l’extension de service.

      Pour recevoir des notifications push enrichies, la première méthode est utilisée :

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


Pour plus d’informations sur les notifications push enrichies avec iOS, voir [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).

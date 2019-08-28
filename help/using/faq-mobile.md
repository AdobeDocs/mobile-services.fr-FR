---
description: Questions fréquentes et réponses relatives à Adobe Mobile Services ainsi qu’une description générale des fonctionnalités.
keywords: mobile
seo-description: Questions fréquentes et réponses relatives à Adobe Mobile Services ainsi qu’une description générale des fonctionnalités.
seo-title: Questions fréquentes
solution: Marketing Cloud, Analytics
title: Questions fréquentes
topic: Mesures
uuid: 62 a 9241 c -2 ada -483 a-a 594-b 023916 cb 0 b 6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Questions fréquentes {#frequently-asked-questions}

Le tableau suivant contient la liste des questions fréquentes pour Adobe Mobile Services :

## SDK Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Mettez-vous fréquemment à jour le SDK ?

Oui. Afin de vous proposer des SDK riches en fonctions, sécurisés et conformes, nous les mettons constamment à jour. En général, une nouvelle version est publiée chaque mois. Ces mises à jour de SDK sont des kits de substitution (pour la version 4x) visant à faciliter la mise en œuvre. Pour de plus amples informations sur nos mises à jour, consultez nos [Notes de mise à jour](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Quelle version de SDK dois-je avoir installée ?

Actuellement, nous proposons des SDK version 4.11. Pour de plus amples informations, consultez nos [Notes de mise à jour](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Où puis-je télécharger les SDK ?

Vous pouvez télécharger les kits SDK pour les plateformes mobiles individuelles en visitant la section [Gérer les paramètres](/help/using/c-manage-app-settings/c-manage-app-settings.md) de l'application.

### Comment configurer les SDK ?

Après avoir créé une suite de rapports d'applications, accédez à Gérer les paramètres d'application et configurez toutes les options requises sur la page d'informations de l'application. Après avoir enregistré la configuration, téléchargez les SDK requis répertoriés dans le bas de la page Gérer les paramètres de l’application. The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Les SDK Adobe Mobile sont-ils compatibles avec le protocole IPv6 pour iOS ?

Les SDK Adobe Mobile utilisent les piles réseau iOS et Android standard. Pour ios, le SDK utilise nsurlsession (ios versions 7 +) et nsurlconnection (ios versions 7 et ultérieures) qui sont entièrement compatibles avec ipv 6. Les développeurs qui ont créé ou utilisé leur propre pile réseau peuvent vérifier s'il existe d'autres considérations d'atténuation. Voici quelques informations supplémentaires d'Apple :

*Si vous créez une application côté client à l'aide d'API réseau de haut niveau, telles que nsurlsession et les structures cfnetwork, et que vous vous connectez par nom, vous ne devez rien modifier pour que votre application fonctionne avec les adresses ipv 6.* Pour plus d'informations, [voir Prise en charge des réseaux](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)DNS 64/NAT 64.


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Que sont les mesures de cycle de vie ?

Les mesures de cycle de vie sont des mesures prêtes à l’emploi, automatiquement collectées lors de la première mise en œuvre du SDK dans votre application. Pour plus d'informations, voir [Mesures de cycle de vie (Android)](/help/android/metrics.md) et [Mesures de cycle de vie (ios)](/help/ios/metrics.md).

### Comment puis-je résoudre les problèmes liés aux règles de traitement ?

Pour en savoir plus, voir [Conseils et astuces sur les règles de traitement](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Puis-je envoyer mes données d’analyse à plusieurs suites de rapports ?

Oui. Les SDK offrent la possibilité d’envoyer des données à plusieurs suites de rapports Adobe Analytics. Pour enregistrer les données issues de plusieurs suites de rapports à l’aide d’une demande d’image, définissez les ID de ces suites de rapports dans le champ **[!UICONTROL rsids]** dans la section **Analytics[!UICONTROL dans le fichier , en les délimitant par des virgules, sans espaces.]**`ADBMobileConfig.json` Pour plus d'informations, voir [Configuration JSON adbmobile](/help/ios/configuration/json-config/json-config.md).

### En quoi les visites par des dispositifs portables diffèrent-elles des lancements ?

Un lancement se mesure en fonction du SDK quand un utilisateur ouvre l’application pour la première fois ou revient à l’application après l’avoir quittée pendant plus longtemps que la valeur de temporisation spécifiée. The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. Une visite est un calcul d’Adobe Analytics côté serveur, d’après le premier et le dernier accès aux données envoyées par le SDK sans dépasser le délai de temporisation d’une visite. En général, pour une suite de rapports, une session expire après 30 minutes. Bien que ces visites soient issues d’une analyse Web traditionnelle, ces accès offrent toujours des connaissances utiles sur la façon dont les utilisateurs lancent et quittent votre application.

## Messagerie {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Existe-t-il des limitations de taille ou autres à propos des notifications push ?

Les messages de notification push sont limités à 140 caractères. Il n’existe aucune limitation quant au nombre de notifications pouvant être envoyées ou planifiées ni à la façon dont les notifications sont envoyées.

### Les données utiles personnalisées sont-elles prises en charge pour les notifications push ?

Oui. Nous fournissons des données utiles push personnalisées qui peuvent être codées dans l’objet JSON. Les données utiles Android et iOS sont limitées à 4 ko et à 2 ko, respectivement. Elles sont envoyées à l’application par l’intermédiaire d’une notification push ou locale. Pour plus d'informations, voir [Expérience : Message Push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Les messages in-app sont-ils limités en taille ?

Les messages in-app publiés et actifs créés dans Adobe Mobile Services sont hébergés sur un serveur ; chaque suite de rapports d’application est limitée à 15 Mo. Cette restriction s’applique au contenu des messages et aux ressources hébergées par Adobe. Toutefois, il n’existe aucune restriction quant au type de ressources d’autres hôtes ou de l’application même auxquelles le message in-app peut se référer.

### Puis-je utiliser mon propre code HTML pour les messages in-app ?

Oui. Le code HTML personnalisé est pris en charge pour vos messages in-app. For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Quels déclencheurs puis-je utiliser pour envoyer des notifications push ou des messages in-app ?

Les marketeurs peuvent choisir quels événements ou données Analytics sont envoyés pour déclencher l’affichage des messages in-app. Les messages in-app utilisent des déclencheurs qui surviennent localement sur le périphérique. Si vous sélectionnez plusieurs déclencheurs, ils doivent tous survenir sur le même accès pour que le message s’affiche. For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Les messages push sont envoyés en utilisant les segments prédéfinis d’Adobe Analytics ou les segments personnalisés qui peuvent être créés pour les données Analytics historiques déjà collectées. Pour plus d'informations, voir [Expérience : Message Push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Pourquoi puis-je obtenir une erreur avec le nom in-app, push ou marketing que j'ai saisi ?

Vous ne pouvez pas utiliser le même nom pour le message in-app, push ou le lien marketing dans différentes applications qui utilisent la même suite de rapports virtuelle (VRS) parente. Pour résoudre ce problème, saisissez un autre nom pour votre message in-app, votre message Push ou votre lien marketing.

## Emplacement {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Le nombre d'oints d'intérêt (POI) peut-il être limité ?

Il n’y a aucune restriction spécifique, mais pour des performances idéales et en raison de restrictions de mémoire sur l’appareil de l’utilisateur, nous recommandons de créer et de télécharger un maximum de 5 000 points ciblés.

## Acquisition {#section_B37F1129CD5843E890D0E54179455357}

### Puis-je attribuer des campagnes aux activités in-app ?

Oui. Adobe Mobile Services peut vous aider à créer des mécanismes marketing qui vous aideront à convertir et à orienter le trafic vers vos applications et à lier les campagnes d’acquisition aux analyses et conversions in-app. Pour plus d’informations, voir [Acquisition](/help/using/acquisition-main/acquisition-main.md).

### Comment puis-je configurer des liens pour gagner de nouveaux utilisateurs de l’application et en faire le suivi.

Vous pouvez créer des liens marketing qui incitent les utilisateurs à télécharger des applications à partir de l'Apple App Store et de Google Play. Ces liens permettent d’attribuer les événements de succès aux téléchargements. Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).
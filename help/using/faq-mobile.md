---
description: Questions fréquentes et réponses relatives à Adobe Mobile Services ainsi qu’une description générale des fonctionnalités.
keywords: mobile
seo-description: Questions fréquentes et réponses relatives à Adobe Mobile Services ainsi qu’une description générale des fonctionnalités.
seo-title: Questions fréquentes
solution: Experience Cloud,Analytics
title: Questions fréquentes
topic-fix: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
exl-id: d7dfc36e-56f0-498a-ad50-93fee90cb6ff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 100%

---

# Questions fréquentes {#frequently-asked-questions}

Le tableau suivant contient la liste des questions fréquentes sur Adobe Mobile Services :

## SDK Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Effectuez-vous des mises à jour fréquentes avec le SDK ?

Oui, nous faisons constamment des mises à jour afin de vous offrir les SDK les plus riches en fonctionnalités, les plus conformes aux normes et les plus sécurisés. En général, nous publions une nouvelle version tous les mois. Ces mises à jour du SDK sont des remplacements directs (pour la version 4x) afin de faciliter la mise en œuvre. Pour plus d’informations sur nos mises à jour, consultez nos [notes de mise à jour](https://docs.adobe.com/content/help/fr-FR/release-notes/experience-cloud/current.html).

### Quelle version de SDK dois-je avoir installée ?

Nos SDK actuels sont sur la version 4.11. Pour plus d’informations, consultez nos [notes de mise à jour](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Où puis-je télécharger les SDK ?

Les SDK de plateformes mobiles individuelles peuvent être téléchargés en consultant la section [Gestion des paramètres de l’application](/help/using/c-manage-app-settings/c-manage-app-settings.md).

### Comment configurer les SDK ?

Après avoir créé une suite de rapports d’application, accédez à Gestion des paramètres de l’application et configurez toutes les options requises sur la page d’informations de l’application. Après avoir enregistré la configuration, téléchargez les SDK requis répertoriés dans le bas de la page Gérer les paramètres de l’application. Le SDK est préconfiguré avec les options que vous avez enregistrées. Il se trouve dans le fichier `ADBMobileConfig.json` dans le package du SDK. Si vous modifiez les paramètres du SDK sur la page Gestion des paramètres de l’application, veillez à télécharger à nouveau les fichiers du SDK ou à apporter les modifications nécessaires au fichier `ADBMobileConfig.json`.

### Les SDK Adobe Mobile prennent-ils en charge le protocole IPv6 pour iOS ?

Les SDK Adobe Mobile utilisent les piles réseau iOS et Android standard. Pour iOS, le SDK utilise NSURLSession (iOS versions 7+) et NSURLConnection (iOS versions 7 et ultérieure), qui sont entièrement compatibles avec le protocole IPv6. Les développeurs qui ont créé ou qui utilisent leur propre pile réseau devront peut-être vérifier si d’autres facteurs d’atténuation sont à prendre en compte. Voici quelques informations supplémentaires de la part d’Apple :

*Si vous rédigez une application côté client à l’aide des API réseau de haut niveau, telles que les structures NSURLSession et CFNetwork, et que vous ouvrez une session par nom, vous ne devriez avoir à changer aucun paramètre pour que votre application fonctionne avec les adresses IPv6.* Pour plus d’informations, voir l’article [Supporting IPv6 DNS64/NAT64 Networks](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1) (en anglais).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Que sont les mesures de cycle de vie ?

Les mesures de cycle de vie sont des mesures prêtes à l’emploi qui sont automatiquement collectées lors de la première mise en œuvre du SDK dans votre application. Pour plus d’informations, voir [Mesures de cycle de vie (Android)](/help/android/metrics.md) et [Mesures de cycle de vie (iOS)](/help/ios/metrics.md).

### Comment puis-je résoudre les problèmes liés aux règles de traitement ?

Pour plus d’informations, voir [Astuces et conseils concernant les règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Puis-je envoyer mes données d’analyse à plusieurs suites de rapports ?

Oui. Les SDK permettent d’envoyer des données à plusieurs suites de rapports Adobe Analytics. Pour enregistrer les données issues de plusieurs suites de rapports à l’aide d’une demande d’image, définissez les ID de ces suites de rapports dans le champ **[!UICONTROL rsids]** dans la section **[!UICONTROL Analytics]** dans le fichier `ADBMobileConfig.json`, en les délimitant par des virgules, sans espaces. Pour plus d’informations, voir [Configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

### En quoi les visites Mobile diffèrent-elles des lancements ?

Un lancement est mesuré par le SDK lorsqu’un utilisateur ouvre l’application pour la première fois ou revient à l’application après l’avoir quittée pendant plus longtemps que la valeur de délai d’expiration spécifiée. Le délai d’expiration type est de 5 minutes (300 secondes) dans le champ **[!UICONTROL lifecycleTimeout]** situé dans le fichier `ADBMobileConfig.json`. Une visite est un calcul côté serveur effectué par Adobe Analytics et est basé sur les premiers et derniers accès aux données envoyés par le SDK sans dépasser le délai d’expiration d’une visite. En règle générale, les délais d’expiration de session sont définies sur 30 minutes pour une suite de rapports. Bien que les visites proviennent des analyses web traditionnelles, ces accès fournissent quand même des informations précieuses sur la manière dont les utilisateurs entrent et sortent de votre application.

## Messagerie {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Existe-t-il des limitations de taille ou autres sur les notifications push ?

Les messages de notification push sont limités à 140 caractères. Il n’existe aucune limite quant au nombre de notifications pouvant être envoyées ou planifiées ou à la fréquence d’envoi des notifications.

### Prenez-vous en charge des payloads personnalisées pour les notifications push ?

Oui, nous fournissons une payload push personnalisée qui peut être codée dans JSON. Les payloads Android et iOS sont limitées à 4 Ko et à 2 Ko, respectivement. Ces payloads sont envoyées à l’application par le biais d’une notification push ou locale. Pour plus d’informations, voir [Experience : Message push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Les messages in-app sont-ils limités en taille ?

Les messages in-app publiés et actifs créés dans Adobe Mobile Services sont hébergés sur un serveur avec une limite de taille de 15 Mo par suite de rapports d’application. Bien que cette restriction s’applique au contenu des messages et aux ressources hébergées sur Adobe, il n’existe aucune restriction quant aux ressources auxquelles le message in-app peut faire référence sur d’autres hôtes ou sur celles de l’application.

### Puis-je utiliser mon propre code HTML pour les messages in-app ?

Oui, nous prenons en charge le code HTML personnalisé pour vos messages in-app. Pour plus d’informations, voir [Experience : Message in-app](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Quels déclencheurs puis-je utiliser pour envoyer des notifications push ou des messages in-app ?

Les marketeurs peuvent choisir n’importe quel événement ou donnée Analytics envoyé comme déclencheur pour afficher les messages in-app. Les messages in-app utilisent des déclencheurs qui se produisent localement sur l’appareil. Si plusieurs déclencheurs sont sélectionnés, tous les déclencheurs doivent se produire dans le même accès pour que le message s’affiche. Pour plus d’informations, voir [Experience : Message in-app](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Les messages push sont envoyés en utilisant les segments prédéfinis d’Adobe Analytics ou les segments personnalisés qui peuvent être créés pour les données Analytics historiques déjà collectées. Pour plus d’informations, voir [Experience : Message push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Pourquoi y a-t-il une erreur avec le nom du message in-app, push ou du lien marketing que j’ai saisi ?

Vous ne pouvez pas utiliser le même nom pour le message in-app, push ou le lien marketing dans différentes applications qui utilisent la même suite de rapports virtuelle (VRS) parente. Pour résoudre cette erreur, saisissez un autre nom pour votre message in-app, push ou votre lien marketing.

## Emplacement {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Le nombre de points ciblés que je peux définir est-il limité ?

Il n’y a aucune restriction spécifique, mais pour des performances idéales et en raison de restrictions de mémoire sur l’appareil de l’utilisateur, nous recommandons de créer et de télécharger un maximum de 5 000 points ciblés.

## Acquisition {#section_B37F1129CD5843E890D0E54179455357}

### Puis-je attribuer des campagnes aux activités in-app ?

Oui. Adobe Mobile Services peut vous aider à créer des astuces marketing qui aident à promouvoir et à diriger le trafic vers vos applications et à lier les campagnes d’acquisition aux analyses et conversions in-app. Pour en savoir plus, consultez la rubrique [Acquisition](/help/using/acquisition-main/acquisition-main.md).

### Comment puis-je configurer des liens pour gagner de nouveaux utilisateurs de l’application et en faire le suivi ?

Vous pouvez créer des liens marketing qui incitent les utilisateurs à télécharger des applications à partir de l’App Store Apple et de Google Play. Ces liens permettent d’attribuer les événements de succès aux téléchargements. Pour obtenir plus d’informations, voir [Générateur de liens marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

---
description: Vous pouvez définir et configurer les options d’audience se rapportant aux messages push, y compris la période, les segments Analytics et les segments personnalisés.
keywords: mobile
seo-description: Vous pouvez définir et configurer les options d’audience se rapportant aux messages push, y compris la période, les segments Analytics et les segments personnalisés.
seo-title: Audience  Define and Configure Audience Segments for Push Messages
solution: Marketing Cloud,Analytics
title: Audience Définir et configurer des segments d’audience pour les messages push
topic: Mesures
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# Audience: push messages{#audience-define-and-configure-audience-segments-for-push-messages}

Vous pouvez définir et configurer les options d’audience se rapportant aux messages push, y compris la période, les segments Analytics et les segments personnalisés.

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

Lorsqu’un segment d’audience est créé pour les messages push, le segment peut inclure des utilisateurs d’une ou plusieurs applications, car les suites de rapport ou suites de rapports virtuelles peuvent contenir des données concernant une ou plusieurs applications. Pour de plus amples informations concernant les suites de rapports virtuelles, voir [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

Dans Adobe Mobile Services, les marketeurs peuvent uniquement pousser les données vers une seule application par plateforme. Si les marketeurs tentent de les pousser vers des segments qui contiennent des utilisateurs issus de plusieurs applications, un avertissement s’affiche et indique que cette opération peut entraîner de graves dysfonctionnements des messages push, ainsi que l’inscription potentielle de certains utilisateurs sur liste noire. Si vous êtes confronté à un dysfonctionnement des messages push, consultez *Résoudre les dysfonctionnements des messages push* dans [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Afin d’utiliser les données Audience Manager dans votre définition de segment, consultez [Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

If you select an audience segment that contains users across multiple apps, you might see the following alert:

![plusieurs noms d’application](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>Le numéro de version est facultatif.

Au maximum, six ensembles de chiffres pour la version et cinq ensembles pour l’identification du lot sont supprimés.

Par exemple :

* `Bea[rd]cons 1.0 (123)` will appear as `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` apparaît comme `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` will appear as `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` will appear as `Bea[rd]cons (.6)`

Pour continuer à envoyer des messages push aux applications énumérées, cochez la case **Oui, je souhaite poursuivre.** puis cliquez sur **[!UICONTROL Envoyer]**.

## Bonnes pratiques

Voici quelques bonnes pratiques à retenir :

* Pour diminuer les risques de confusion, **évitez** de définir des suites de rapports virtuelles pour application mobile qui contiennent des données issues de plusieurs applications.
* Utilisez un ID d’application unique intégré à un segment d’audience **à chaque fois** que vous souhaitez envoyer un message push.
Cette méthode garantit que les notifications push sont envoyées à un segment d’audience qui n’appartient qu’à **une seule** application.

### Exemples

Voici quelques exemples pour vous aider à comprendre comment définir des segments correctement :

**À faire** : le marketeur fournit des certificats push pour les versions iOS et Android d’une application, par exemple, pour Adobe Photoshop. Le marketeur peut envoyer une notification push à un segment d’utilisateurs qui concerne les deux plateformes.

**À ne pas faire** : le marketeur fournit des certificats push pour les versions iOS et Android d’une application, par exemple, pour Adobe Photoshop. Si le marketeur crée et envoie un message à *tous les utilisateurs actifs au cours des 30 derniers jours*, seuls les utilisateurs de l’application Adobe Photoshop sur iOS et Android recevront le message push, tous les utilisateurs de l’application Adobe Illustrator sur iOS et Android seront inscrits sur liste noire. Pour de plus amples informations et exemples, consultez *Résoudre les dysfonctionnements des messages push* dans [Résolution des problèmes liés aux messages push](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. Go to the Audience page for a new push message.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * L’**[!UICONTROL Audience estimée ayant souscrit]** est le nombre d’appareils qui correspondent au segment Adobe Analytics **et** le nombre d’appareils ayant accepté les messages.

      Vous pouvez afficher une estimation du nombre d’utilisateurs membres de vos segments sélectionnés qui ont choisi de recevoir des messages et qui recevront le message push. Le nombre total d’utilisateurs de l’application s’affiche en dessous de l’estimation, indépendamment du statut de souscription.

   * Le **[!UICONTROL Total]est le nombre d’appareils qui correspondent au segment Adobe Analytics.**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      This means that the SDK has sent a value of `True` for the Push Message Opt-In evar.

   * Même si le périphérique dispose d’un jeton de périphérique valide, à moins qu’Adobe Analytics n’ait défini l’indicateur d’inclusion, le message n’est pas envoyé au périphérique.

   * Pour de plus amples informations sur la résolution des problèmes liés aux messages push, consultez ceci :

      * [Push messaging in iOS](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Push messaging in Android](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. Renseignez les champs suivants :

   * **[!UICONTROL Durant :]**

      Spécifiez la plage temporelle à utiliser pour l’audience estimée. Sélectionnez une option dans la liste déroulante **[!UICONTROL Durant] :**

   * **[!UICONTROL L’option Dernier(s)]** vous permet de sélectionner une plage temporelle relative (par exemple, les 7 derniers jours, les 30 derniers jours ou les 60 derniers jours) à partir du moment où l’envoi du message push est programmé.

      À titre d’exemple, si vous sélectionnez les 30 derniers jours et programmez l’envoi du message push le 31 octobre, l’audience estimée correspondra au nombre d’utilisateurs qui ont choisi de recevoir les messages push au cours des 30 jours qui précèdent le 31 octobre.

   * **[!UICONTROL L’option Plage statique]** vous permet de sélectionner une plage statique en sélectionnant les dates de début et de fin pour la gamme d’audience estimée.

      En reprenant l’exemple précédent, si vous sélectionnez une plage de dates commençant le 1er octobre et se terminant le 15 octobre, mais planifiez le message push le 31 octobre, l’audience estimée correspondra au nombre d’utilisateurs qui ont choisi de recevoir les messages push dans la plage de dates statique spécifiée (du 1er au 15 octobre).

   * **[!UICONTROL Segments Analytics]**

      Select an existing Adobe Analytics segment from the drop-down list. For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL Segments personnalisés]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. À titre d’exemple, le segment personnalisé suivant cible les utilisateurs possesseurs d’un téléphone mobile exécutant iOS et situés dans la région de la Californie (États-Unis).
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

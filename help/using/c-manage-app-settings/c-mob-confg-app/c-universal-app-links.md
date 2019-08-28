---
description: Les liens universels (ios) et les liens d'application (Android) vous permettent de vous connecter à des liens profonds dans vos applications ios ou Android.
keywords: mobile
seo-description: Les liens universels (ios) et les liens d'application (Android) vous permettent de vous connecter à des liens profonds dans vos applications ios ou Android.
seo-title: Liens Apple Universal Links et Android App Links
solution: Marketing Cloud, Analytics
title: Liens Apple Universal Links et Android App Links
topic: Mesures
uuid: 8 d 6441 dc -4307-4454-95 ea-d 77 ec 796 f 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Liens Apple Universal Links et Android App Links{#universal-links-and-app-links}

Les liens universels (ios) et les liens d'application (Android) vous permettent de vous connecter à des liens profonds dans vos applications ios ou Android.

>[!IMPORTANT]
>
>À compter d'ios 9.2, la création de liens profonds n'est pas prise en charge. Vous devez utiliser les liens universels Apple pour créer des liens profonds vers votre application ou votre site Web.

## Liens universels {#section_F8147944679A42E59CF4FD8814E5EF12}

Les liens universels vous permettent de vous connecter aux liens profonds dans votre application ios et sont pris en charge sous ios 9.2 ou version ultérieure. Lorsqu'un lien universel est atteint, ios redirige directement le lien vers le lien profond dans votre application. Si votre application n'est pas installée, elle ouvre une URL pour votre site Web dans un navigateur. Pour plus d'informations sur les liens universels, voir [Prise en charge des liens universels](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Liens d'application

Les liens d'application vous permettent de vous connecter aux liens profonds dans votre application Android et sont pris en charge dans Android 6.0 ou version ultérieure. Lorsque vous accédez à un lien d'application, Android redirige directement le lien vers le lien profond dans votre application. Si votre application n'est pas installée, elle ouvre une URL pour votre site Web dans un navigateur. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Création d'un lien marketing à l'aide d'un lien universel ou d'application {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Vous pouvez créer un lien marketing qui utilise un lien universel ou d'application.

### Configuration d'un lien universel

1. Pour configurer les liens universels dans votre application ios, accédez [à Gestion des liens universels dans Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Dans Adobe Mobile Services, configurez les documents d'association de site :

   a. Dans la page d'accueil Services mobiles, sélectionnez l'application pour laquelle vous souhaitez configurer les liens universels.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Assurez-vous que l'application ios qui gère les liens universels est ajoutée à la section **[!UICONTROL Ajouter des applications]** de boutique d'applications.

   >[!TIP]
   >
   >Si la section **[!UICONTROL Ajouter des applications]** de boutique d'applications ne s'affiche pas, cliquez sur le lien **[!UICONTROL Ajouter une application]** de boutique d'applications.

   d. Dans la section Options **[!UICONTROL des liens universels et d'application, sélectionnez]** une application ios et saisissez l'ID de l'application.

   f. Cliquez **[!UICONTROL sur Enregistrer]**.

   Vous devez fournir au moins une sélection d'applications ios et un ID d'application, ou vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur Mettre à jour dans la section Options des liens universels et d’application. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Utilisation d'un lien universel

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise les liens universels :

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Cliquez **[!UICONTROL sur Créer nouveau]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Si vous avez configuré les documents d'association de site dans la section *Définition - vers le haut des documents d'association de site dans la section Adobe* Mobile Services ci-dessus, cette option est sélectionnée par défaut.

   Si vous n'avez pas configuré les documents, l'option **[!UICONTROL Utiliser des liens universels ou d'application]** est désactivée et **[!UICONTROL l'option Utiliser des spots]** est sélectionnée par défaut.

   e. Si l'option **[!UICONTROL Utiliser des liens universels ou d'application]** est sélectionnée, le champ Chemin **[!UICONTROL d'accès]** personnalisé s'affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez `my/universal/link?os=9.2`, votre URL de lien marketing complet devient `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Cliquez sur l'onglet **[!UICONTROL Décisions]** et configurez l'arborescence de décision.

   h. Si l'application ios est installée, l'application gère le lien profond avec sa logique. La destination finale sert uniquement de secours lorsque l'application n'est pas installée. Puisque l'application n'est pas installée, la destination finale ne peut être qu'un lien Web ou une boutique d'applications.

   i. Cliquez **[!UICONTROL sur Enregistrer]**.

>[!TIP]
>
>Une fois qu'un lien marketing est enregistré, les options de liens marketing ne peuvent pas être modifiées. Cela est dû au fait que vous ne souhaitez pas modifier le comportement des liens marketing qui ont peut-être déjà été distribués.


### Configuration d'un lien d'application

1. Pour configurer les liens d'application dans votre application Android, cliquez [sur Ajouter des liens d'application Android](https://developer.android.com/studio/write/app-link-indexing).

1. Dans Adobe Mobile Services, configurez les documents d'association de site :

   a. Dans la page d'accueil Services mobiles, sélectionnez l'application pour laquelle vous souhaitez configurer les liens d'application.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Assurez-vous que l'application Android qui gère les liens universels ou d'application est ajoutée à la section **[!UICONTROL Ajouter des applications]** de boutique d'applications.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Faites défiler la section Options **[!UICONTROL des liens universels et]** d'application.

   e. Cliquez sur l'onglet Liens **[!UICONTROL d'application (Android)]** .

   f. Sélectionnez une application Android et saisissez une empreinte de certificat SHA -256.

   g. Cliquez **[!UICONTROL sur Enregistrer]**.

   Vous devez fournir au moins une sélection d'applications Android et un certificat SHA -256, ou vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur **[!UICONTROL Mettre à jour]** dans la section **Options des liens universels et d’application[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Utilisation d'un lien d'application

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise les liens d'application :

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Cliquez **[!UICONTROL sur Créer nouveau]**.

   c. Dans **[!UICONTROL la section Options]** de lien marketing, sélectionnez **[!UICONTROL Utiliser des liens universels ou d'application]**.

   d. Si vous avez configuré les documents d'association de site à l'étape 2, cette option est sélectionnée par défaut.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Si **[!UICONTROL l'option Utiliser des liens universels ou d'application]** est sélectionnée, **[!UICONTROL le champ Chemin]** personnalisé s'affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez `my/app/link?os=6.0`, votre URL de lien marketing complet devient `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Cliquez sur l'onglet **[!UICONTROL Décisions]** et configurez l'arborescence de décision.

   g. Si l'application Android est installée, l'application gère le lien profond avec sa logique.

   La destination finale sert uniquement de casse de secours lorsque l'application n'est pas installée. Puisque l'application n'est pas installée, la destination finale ne peut être qu'un lien Web ou une boutique d'applications.

   h. Cliquez **[!UICONTROL sur Enregistrer]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Cela est dû au fait que vous ne souhaitez pas modifier le comportement des liens marketing qui ont peut-être déjà été distribués.

## Utilisation des liens marketing

Vous pouvez maintenant utiliser ces liens marketing dans les messages et dans d'autres zones de votre application.

>[!IMPORTANT]
>
>Vous ne verrez pas le suivi des clics avec des liens universels ou d'application, et vous ne pouvez pas utiliser de spots.


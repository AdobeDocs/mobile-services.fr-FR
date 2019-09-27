---
description: Les liens universels (iOS) et les liens d’application (Android) vous permettent de vous connecter à des liens profonds dans vos applications iOS ou Android.
keywords: mobile
seo-description: Les liens universels (iOS) et les liens d’application (Android) vous permettent de vous connecter à des liens profonds dans vos applications iOS ou Android.
seo-title: Liens universels Apple et liens d’application Android
solution: Marketing Cloud,Analytics
title: Liens universels Apple et liens d’application Android
topic: Mesures
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Liens universels Apple et liens d’application Android{#universal-links-and-app-links}

Les liens universels (iOS) et les liens d’application (Android) vous permettent de vous connecter à des liens profonds dans vos applications iOS ou Android.

>[!IMPORTANT]
>
>Depuis iOS 9.2, les liens profonds ne sont pas pris en charge. You must use Apple Universal Links for deep linking to your app or website.

## Liens universels {#section_F8147944679A42E59CF4FD8814E5EF12}

Les liens universels vous permettent de vous connecter à des liens profonds dans votre application iOS et sont pris en charge dans iOS 9.2 ou version ultérieure. Lorsqu’un lien universel est accessible, iOS redirige directement le lien vers le lien profond dans votre application. Si votre application n’est pas installée, elle ouvre plutôt une URL pour votre site Web dans un navigateur. Pour plus d’informations sur les liens universels, voir [Prise en charge des liens](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)universels.

## App Links

Les liens d’application vous permettent de vous connecter à des liens profonds dans votre application Android et sont pris en charge sous Android 6.0 ou version ultérieure. Lorsqu’un lien d’application est accessible, Android le redirige directement vers le lien profond dans votre application. Si votre application n’est pas installée, elle ouvre plutôt une URL pour votre site Web dans un navigateur. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Création d’un lien marketing à l’aide d’un lien universel ou d’application {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Vous pouvez créer un lien marketing qui utilise un lien universel ou d’application.

### Configuration d’un lien universel

1. Pour configurer des liens universels dans votre application iOS, accédez à [Gestion des liens universels dans Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Dans Adobe Mobile Services, configurez les documents d’association de site :

   a. Dans la page d’accueil de Mobile Services, sélectionnez l’application pour laquelle vous souhaitez configurer des liens universels.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Assurez-vous que l’application iOS qui gère les liens universels est ajoutée à la section **[!UICONTROL Ajouter des applications]** de boutique d’applications.

   >[!TIP]
   >
   >Si la section **[!UICONTROL Ajouter des applications]** de boutique d’applications ne s’affiche pas, cliquez sur le lien **[!UICONTROL Ajouter une application]** de boutique d’applications.

   d. Dans la section Options **[!UICONTROL des liens]** universels et d’application, sélectionnez une application iOS et saisissez l’ID de l’application.

   f. Cliquez sur **[!UICONTROL Enregistrer]**.

   Vous devez indiquer au moins une sélection d’applications iOS et un ID d’application, sinon vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur Mettre à jour dans la section Options des liens universels et d’application. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Utilisation d’un lien universel

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise des liens universels :

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. If you configured the site-association documents in the *Setting up site-association documents in Adobe Mobile Services* section above, this option is selected by default.

   Si vous n’avez pas configuré les documents, l’option **[!UICONTROL Utiliser des liens universels ou d’application]** est désactivée et **[!UICONTROL Utiliser des spots]** est sélectionnée par défaut.

   e. Si l’option **[!UICONTROL Utiliser des liens universels ou d’application]** est sélectionnée, le champ Chemin **** personnalisé s’affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez , your full Marketing Link URL becomes .`my/universal/link?os=9.2``https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`

   f. Cliquez sur l'onglet **[!UICONTROL Décisions]** et configurez votre arbre de décision.

   h. If the iOS app is installed, the app handles the deeplink with its logic. The final destination serves only as the fallback when the app is not installed. Since the app is not installed, the final destination can only be a web link or app store.

   i. Click Save.****

>[!TIP]
>
>Once a Marketing Link is saved, the Marketing Links Options cannot be altered. En effet, vous ne souhaitez pas modifier le comportement des liens marketing qui ont peut-être déjà été distribués.


### Configure an App Link

1. To set up App Links in your Android app, go to Add Android App Links.[](https://developer.android.com/studio/write/app-link-indexing)

1. In Adobe Mobile Services, set up the site-association documents:

   a. Dans la page d’accueil de Mobile Services, sélectionnez l’application pour laquelle vous souhaitez configurer les liens d’application.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the Android app that handles Universal Links or App Links is added to the Add App Store Apps section.****

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Accédez à la section Options **[!UICONTROL des liens]** universels et d’application.

   e. Click the App Links (Android) tab.****

   f. Sélectionnez une application Android et saisissez une empreinte numérique de certificat SHA-256.

   g. Cliquez sur **[!UICONTROL Enregistrer]**.

   Vous devez fournir au moins une sélection d’applications Android et un certificat SHA-256, sinon vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur **[!UICONTROL Mettre à jour]** dans la section **Options des liens universels et d’application[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Use an App Link

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise les liens d’application :

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Cliquez sur **[!UICONTROL Créer]**.

   c. Dans la section Options **[!UICONTROL de lien]** marketing, sélectionnez **[!UICONTROL Utiliser des liens universels ou des liens]** d’application.

   d. Si vous avez configuré les documents d’association de site à l’étape 2, cette option est sélectionnée par défaut.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Si **[!UICONTROL Utiliser des liens universels ou d’application]** est sélectionné, le champ Chemin **** personnalisé s’affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez `my/app/link?os=6.0`, l’URL complète du lien marketing devient `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Cliquez sur l'onglet **[!UICONTROL Décisions]** et configurez votre arbre de décision.

   g. Si l'application Android est installée, l'application gère le lien profond avec sa logique.

   The final destination serves only as the fallback case for when the app is not installed. L’application n’étant pas installée, la destination finale ne peut être qu’un lien Web ou une boutique d’applications.

   h.  Cliquez sur **[!UICONTROL Enregistrer]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. En effet, vous ne souhaitez pas modifier le comportement des liens marketing qui ont peut-être déjà été distribués.

## Utilisation des liens marketing

Vous pouvez désormais utiliser ces liens marketing dans les messages et d’autres zones de votre application.

>[!IMPORTANT]
>
>Vous ne verrez pas le nombre de suivi des clics avec des liens universels ou d’application, et vous ne pouvez pas non plus utiliser de spots.


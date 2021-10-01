---
description: La liaison dans les applications et les sites web est importante pour préserver l’expérience utilisateur. Découvrez comment les liens universels et d’application fonctionnent et les différences entre eux.
solution: Experience Cloud,Analytics
title: Guide des liens universels et d’application
topic-fix: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
exl-id: 6613189f-7a14-4066-89e9-996d4fe7f128
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 96%

---

# Liens universels et liens d’application : Comment fonctionnent-ils ? {#universal-links-and-app-links}

Les liens universels (iOS) et les liens d’application (Android) vous permettent de vous connecter à des liens profonds dans vos applications iOS ou Android.

>[!IMPORTANT]
>
>Depuis iOS 9.2, les liens profonds ne sont pas pris en charge. Vous devez utiliser les liens universels Apple pour créer des liens profonds vers votre application ou votre site Web.

## Liens universels {#section_F8147944679A42E59CF4FD8814E5EF12}

Les liens universels vous permettent de vous connecter à des liens profonds dans votre application iOS et sont pris en charge dans iOS 9.2 ou version ultérieure. Lorsqu’un lien universel est accessible, iOS redirige directement le lien vers le lien profond dans votre application. Si votre application n’est pas installée, elle ouvre plutôt une URL pour votre site Web dans un navigateur. Pour plus d’informations sur les liens universels, voir [Prise en charge des liens universels](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Liens d’application

Les liens d’application vous permettent de vous connecter à des liens profonds dans votre application Android et sont pris en charge dans Android 6.0 ou version ultérieure. Lorsqu’un lien d’application est accessible, Android le redirige directement vers le lien profond dans votre application. Si votre application n’est pas installée, elle ouvre plutôt une URL pour votre site Web dans un navigateur. Pour plus d’informations sur les liens d’application, voir l’article [Handling Android App Links](https://developer.android.com/training/app-links/index.html) (en anglais).

## Création d’un lien marketing à l’aide d’un lien universel ou d’application {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Vous pouvez créer un lien marketing qui utilise un lien universel ou d’application.

### Configuration d’un lien universel

1. Pour configurer des liens universels dans votre application iOS, voir l’article [Handling Universal Links](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links) (en anglais) sur le site d’Apple.

2. Dans Adobe Mobile Services, configurez les documents d’association de site :

   a. Sur la page d’accueil de Mobile Services, sélectionnez l’application pour laquelle vous souhaitez créer des liens universels.

   b. Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.

   c. Assurez-vous que l’application iOS qui gère les liens universels est ajoutée à la section **[!UICONTROL Ajout d’une application de la boutique d’applications]**.

   >[!TIP]
   >
   >Si la section **[!UICONTROL Ajout d’une application de la boutique d’applications]** ne s’affiche pas, cliquez sur le lien **[!UICONTROL Ajout d’une application de la boutique d’applications]**.

   d. Dans la section **[!UICONTROL Options des liens universels et d’application]**, sélectionnez une application iOS et saisissez l’ID d’application.

   f. Cliquez sur **[!UICONTROL Enregistrer]**.

   Vous devez indiquer au moins une sélection d’applications iOS et un ID d’application, sinon vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur Mettre à jour dans la section Options des liens universels et d’application. Cependant, en cliquant sur **[!UICONTROL Mettre à jour]**, un avertissement vous indique que les liens universels ou d’application que vous avez déjà créés seront affectés.

### Utilisation d’un lien universel

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise des liens universels :

   a. Sélectionnez l’application sur la page d’accueil de Mobile Services, cliquez sur **[!UICONTROL Acquisition]** > **[!UICONTROL Générateur de liens marketing]**.

   b. Cliquez sur **[!UICONTROL Créer]**.

   c. Sous **[!UICONTROL Options de lien marketing]**, sélectionnez **[!UICONTROL Utiliser des liens universels ou d’application]**.

   d. Si vous avez configuré les documents d’association de site dans la section *Configuration des documents d’association de site dans Adobe Mobile Services* ci-dessus, cette option est sélectionnée par défaut.

   Si vous n’avez pas configuré les documents, l’option **[!UICONTROL Utiliser des liens universels ou d’application]** est désactivée et l’option **[!UICONTROL Utiliser des spots]** est sélectionnée par défaut.

   e. Si l’option **[!UICONTROL Utiliser des liens universels ou d’application]** est sélectionnée, le champ **[!UICONTROL Chemin d’accès personnalisé]** s’affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez  `my/universal/link?os=9.2`, l’URL complète du lien marketing devient `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Cliquez sur l’onglet **[!UICONTROL Décisions]** et configurez votre arbre de décision.

   h. Si l’application iOS est installée, l’application gère le lien profond avec sa logique. La destination finale sert uniquement de secours lorsque l’application n’est pas installée. L’application n’étant pas installée, la destination finale ne peut être qu’un lien Web ou une boutique d’applications.

   i. Cliquez sur **[!UICONTROL Enregistrer]**.

>[!TIP]
>
>Une fois un lien marketing enregistré, les options de lien marketing ne peuvent pas être modifiées. En effet, vous ne devez pas modifier le comportement des liens marketing qui peuvent déjà avoir été distribués.


### Configuration d’un lien d’application

1. Pour configurer les liens d’application dans votre application Android, accédez à [Ajout de liens d’application Android](https://developer.android.com/studio/write/app-link-indexing).

1. Dans Adobe Mobile Services, configurez les documents d’association de site :

   a. Sur la page d’accueil de Mobile Services, sélectionnez l’application pour laquelle vous souhaitez créer des liens d’application.

   b. Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]**.

   c. Assurez-vous que l’application Android qui gère les liens universels ou d’application est ajoutée à la section **[!UICONTROL Ajout d’une application de la boutique d’applications]**.

   >[!TIP]
   >
   >Si cette section ne s’affiche pas, cliquez sur le lien **[!UICONTROL Ajout d’une application de la boutique d’applications]**.

   d. Faites défiler jusqu’à la section **[!UICONTROL Options des liens universels et d’application]**.

   e. Cliquez sur l’onglet **[!UICONTROL Liens d’application (Android)]**.

   F. Sélectionnez une application Android et entrez l’empreinte d’un certificat SHA-256.

   g. Cliquez sur **[!UICONTROL Enregistrer]**.

   Vous devez indiquer au moins une sélection d’applications Android et un certificat SHA-256, sinon vous recevrez une erreur.

   >[!IMPORTANT]
   >
   >Vous pouvez mettre à jour les documents en cliquant sur **[!UICONTROL Mettre à jour]** dans la section **[!UICONTROL Options des liens universels et d’application]**. Cependant, en cliquant sur **[!UICONTROL Mettre à jour]**, un avertissement vous indique que les liens universels ou d’application que vous avez déjà créés seront affectés.

### Utilisation d’un lien d’application

1. Dans Adobe Mobile Services, créez un lien marketing qui utilise des liens d’application :

   a. Sélectionnez l’application sur la page d’accueil de Mobile Services, cliquez sur **[!UICONTROL Acquisition]** > **[!UICONTROL Générateur de liens marketing]**.

   b. Cliquez sur **[!UICONTROL Créer]**.

   c. Dans la section **[!UICONTROL Options de lien marketing]**, sélectionnez **[!UICONTROL Utiliser des liens universels ou d’application]**.

   d. Si vous avez configuré les documents d’association de site lors de l’étape 2, l’option est sélectionnée par défaut.

   Dans le cas contraire, l’option **[!UICONTROL Utiliser des liens universels ou d’application]** est désactivée et l’option **[!UICONTROL Utiliser des spots]** est sélectionnée par défaut.

   e. Si **[!UICONTROL Utiliser des liens universels ou d’application]** est sélectionné, le champ **[!UICONTROL Chemin d’accès personnalisé]** s’affiche.

   Il permet aux utilisateurs de définir le chemin d’URL suivant le domaine avec les paramètres de requête appropriés. Par exemple, si vous entrez  `my/app/link?os=6.0`, l’URL complète du lien marketing devient `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Cliquez sur l’onglet **[!UICONTROL Décisions]** et configurez votre arbre de décision.

   g. Si l’application Android est installée, l’application gère le lien profond avec sa logique.

   La destination finale sert uniquement de cas de secours lorsque l’application n’est pas installée. L’application n’étant pas installée, la destination finale ne peut être qu’un lien Web ou une boutique d’applications.

   h. Cliquez sur **[!UICONTROL Enregistrer]**.

>[!TIP]
>
>Une fois un lien marketing enregistré, les **[!UICONTROL Options de lien marketing]** ne peuvent pas être modifiées. En effet, vous ne devez pas modifier le comportement des liens marketing qui peuvent déjà avoir été distribués.

## Utilisation des liens marketing

Vous pouvez désormais utiliser ces liens marketing dans la messagerie et d’autres zones de votre application.

>[!IMPORTANT]
>
>Vous ne verrez pas le nombre de suivi des clics avec des liens universels ou d’application, et vous ne pouvez pas non plus utiliser de spots.

---
description: Les postbacks vous permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.
seo-description: Les postbacks vous permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.
seo-title: Configuration des postbacks
title: Configuration des postbacks
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 71%

---


# Configuration des postbacks {#configure-postbacks}

Les postbacks vous permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En exploitant les mêmes déclencheurs et caractéristiques que ceux utilisés pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Pour utiliser des postbacks, vous devez installer le SDK version 4.6 ou ultérieure. Pour plus d’informations, voir [Android - Postbacks](/help/android/analytics-main/postbacks/postbacks.md) ou [iOS - Postbacks](/help/ios/analytics-main/postback/postback.md).

1. Cliquez sur le nom de l’application souhaitée pour accéder à sa page Gérer les paramètres de l’application, puis cliquez sur le lien **[!UICONTROL Gérer les postbacks]** en haut à droite.
1. Cliquez sur **[!UICONTROL Créer un postback]**.
1. Saisissez les informations suivantes dans les champs :

   * **[!UICONTROL Type de postback]**

      Sélectionnez **[!UICONTROL Personnalisé]**. Des modèles seront disponibles à l’avenir.

   * **[!UICONTROL Nom]**

      Saisissez un nom explicite pour le postback.

   * **[!UICONTROL URL]**

      Spécifiez une adresse URL de point de terminaison valide (avec les paramètres de requête appropriés nécessaires pour les requêtes GET). Cette adresse URL s’obtient auprès de la partie à laquelle vous envoyez les données (serveur publicitaire ou votre propre point de terminaison). Par exemple `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variable contextuelle]**

      Mettez en évidence certaines parties de l’adresse URL et sélectionnez la variable contextuelle souhaitée dans la liste déroulante. Vous pouvez également insérer des variables contextuelles dans l’URL et l’URL remplacera toutes les variables de modèle par les valeurs de l’accès.

   * **[!UICONTROL Ajouter un corps de publication]**

      Spécifiez le contenu du corps de publication complémentaire, par exemple dans une requête Post. Si vous spécifiez le texte de corps de publication, spécifiez le type de contenu lié au corps de publication. Par exemple : `application/json`.

   * **[!UICONTROL Délai d’expiration (en secondes)]**

      Spécifiez la durée (en secondes) d’attente du postback.

   * **[!UICONTROL Déclencheur(s)]**

      Spécifiez une ou plusieurs balises de données et conditions qui déclenchent le postback. Vous pouvez par exemple sélectionner le déclencheur **[!UICONTROL Bloqué]** et la condition **[!UICONTROL Existe]** pour déclencher le postback lorsque l’application se bloque. Vous pouvez également spécifier les mesures qui activent le postback. Vous pouvez par exemple sélectionner le déclencheur **[!UICONTROL Nom de l’appareil]** et les conditions **[!UICONTROL Égal à]** et **[!UICONTROL iPhone 6 Plus]** pour activer le postback lorsque l’application se bloque sur les iPhone 6 Plus.

   * **[!UICONTROL Caractéristique(s)]**
   Choisissez qui verra le message lorsqu’il est déclenché. Options include **[!UICONTROL Session Length]**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour créer le postback et l’ajouter à la liste **[!UICONTROL Gérer les postbacks]**.

   Pour activer le postback ultérieurement, procédez de l’une des manières suivantes :

   * Cochez la case en regard du postback dans la liste **[!UICONTROL Gérer les postbacks]**, puis cliquez sur **[!UICONTROL Activer la sélection]**.
   * Cliquez sur **[!UICONTROL Enregistrer et activer]** pour sauvegarder vos modifications et activer immédiatement le postback.

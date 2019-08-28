---
description: Les postbacks permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.
seo-description: Les postbacks permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.
seo-title: Configuration des postbacks
title: Configuration des postbacks
uuid: a 026575 c -057 b -4868-b 6 c 8-9514 cbc 32 b 4 d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

Les postbacks permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En utilisant les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer Mobile Services pour envoyer des données personnalisées vers une destination tierce.

>[!IMPORTANT]
>
>Pour utiliser les postbacks, vous devez installer le kit SDK 4.6 ou version ultérieure. Pour plus d’informations, voir [Android - Postbacks](/help/android/analytics-main/postbacks/postbacks.md) ou [iOS - Postbacks](/help/ios/analytics-main/postback/postback.md).

1. Cliquez sur le nom de l’application souhaitée pour accéder à sa page Gérer les paramètres de l’application, puis cliquez sur le lien **Gérer les postbacks** en haut à droite.
1. Cliquez sur **[!UICONTROL Créer un postback]**.
1. Saisissez les informations suivantes dans les champs :

   * **[!UICONTROL Type de postback]**

      Sélectionnez **[!UICONTROL Personnalisé]**. Des modèles seront disponibles à l’avenir.

   * **[!UICONTROL Nom]**

      Saisissez un nom explicite pour le postback.

   * **[!UICONTROL URL]**

      Spécifiez une URL de endpoint de terminaison valide (avec les paramètres de requête appropriés si nécessaire pour les requêtes GET). Cette adresse URL s’obtient auprès de la partie à laquelle vous envoyez les données (serveur publicitaire ou votre propre point de terminaison). For example `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variable contextuelle]**

      Mettez en évidence certaines parties de l’adresse URL et sélectionnez la variable contextuelle souhaitée dans la liste déroulante. Vous pouvez également insérer des variables contextuelles dans l'URL et l'URL remplace toutes les variables de modèle par les valeurs de l'accès.

   * **[!UICONTROL Ajouter un corps de publication]**

      Spécifiez le contenu du corps de publication complémentaire, par exemple dans une requête Post. Si vous spécifiez le texte du corps de publication, indiquez le type de contenu du corps de publication. Par exemple : `application/json`.

   * **[!UICONTROL Délai d’expiration (en secondes)]**

      Spécifiez la durée (en secondes) d’attente du postback.

   * **[!UICONTROL Déclencheur(s)]**

      Spécifiez une ou plusieurs balises de données et conditions qui déclenchent le postback. For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. Vous pouvez également spécifier les mesures qui activent le postback. For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL Caractéristique(s)]**
   Choisissez qui verra le message lorsqu’il est déclenché. Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour créer le postback et l’ajouter à la liste **Gérer les postbacks[!UICONTROL .]**

   Pour activer le postback ultérieurement, procédez de l’une des manières suivantes :

   * Cochez la case en regard du postback dans la liste **[!UICONTROL Gérer les postbacks]**, puis cliquez sur **[!UICONTROL Activer la sélection]**.
   * Cliquez sur **[!UICONTROL Enregistrer et activer]pour sauvegarder vos modifications et activer immédiatement le postback.**
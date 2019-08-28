---
description: Vous pouvez configurer les options d’audience pour les messages in-app, y compris les options d’affichage, de déclenchement et de caractéristiques.
keywords: mobile
seo-description: Vous pouvez configurer les options d’audience pour les messages in-app, y compris les options d’affichage, de déclenchement et de caractéristiques.
seo-title: Message in-app d'audience
solution: Marketing Cloud, Analytics
title: Message in-app d'audience
topic: Mesures
uuid: 6 c 815 d 4 c -7626-4 cf 4-9158-3 f 059 c 79317 a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

Vous pouvez configurer les options d’audience pour les messages in-app, y compris les options d’affichage, de déclenchement et de caractéristiques.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Sur la page Audience, saisissez les informations dans les champs suivants :

   * **[!UICONTROL Affichage]**

      Sélectionnez l’option qui déclenchera l’affichage d’un message :

      * **[!UICONTROL Toujours]**

         Avec cette option, le message s’affichera à chaque déclenchement.

      * **[!UICONTROL Une fois]**

         Avec cette option, le message s’affichera au premier déclenchement seulement.

      * **[!UICONTROL Jusqu’au clic]**

         Avec cette option, le message s’affichera à chaque déclenchement, jusqu’à ce que l’utilisateur clique dessus. Ce déclenchement survient uniquement en mode plein écran et pour les messages d’alerte. La plupart des messages doivent rediriger ou utiliser une ressource d’Internet et ne s’afficheront pas hors ligne. Afin de toujours afficher le message, quelle que soit la connectivité au réseau, sélectionnez la case à cocher **[!UICONTROL Afficher hors ligne].**
   * **[!UICONTROL Déclencheur]**

      Sélectionnez une option dans la liste déroulante, puis une condition. Vous pouvez par exemple sélectionner **[!UICONTROL Lancé]** dans la première liste déroulante et **Existe]dans la seconde.[!UICONTROL ** Vous pouvez également spécifier des données contextuelles personnalisées qui doivent figurer dans l’événement de déclenchement pour afficher le message.

      >[!IMPORTANT]
      >
      >Si vous sélectionnez plusieurs déclencheurs, pour que le message s'affiche, tous les déclencheurs doivent survenir sur le même accès.

   * **[!UICONTROL Caractéristiques]**
Vous pouvez déterminer qui doit voir le message in-app lorsqu'il est déclenché et filtrer (segmenter) l'audience vers les accès qui possèdent des données spécifiées. Par exemple, vous pouvez définir une règle selon laquelle les points ciblés contiennent Denver. Ce filtre vous permet d’afficher le message aux clients inclus dans l’un de vos points ciblés contenant Denver dans le nom, au moment du déclenchement.



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>Les déclencheurs et caractéristiques utilisent les données transmises à Analytics à partir de votre application. Ces valeurs sont transférées en tant que données contextuelles, variables mappées et mesures. Une variable est une valeur basée sur du texte alors qu’une mesure est une valeur numérique.

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL Variables et mesures standard]**
* **[!UICONTROL Variables personnalisées]**
* **[!UICONTROL Mesures personnalisées]**

Une fois le mappage validé, sélectionnez le comparateur approprié ou un opérateur logique afin de configurer votre audience pour le message.

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![options de déclenchement](assets/custom_trigger_matcher_options.png)

Les scénarios suivants vous aident à déterminer si une mesure ou une variable est sélectionnée comme déclencheur :

### Mesures

Une mesure est un nombre, il peut s’agir par exemple d’un nombre dʼachats.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Procédez comme suit dans la section **[!UICONTROL Déclencheur]** de l’onglet **Audience[!UICONTROL  :]**

   1. Sélectionnez un événement standard tel que **[!UICONTROL Lancé]** et sélectionnez **[!UICONTROL Existe]**.
   1. Sélectionnez un second déclencheur qui est un point de données personnalisé mappé à une mesure.
   1. Under **[!UICONTROL Number]**, select a matcher option.

### Variables

Une variable est une chaîne de texte, c’est un identifiant unique. On peut citer par exemple des pays, des aéroports, etc.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Procédez comme suit dans la section **[!UICONTROL Déclencheur]** de l’onglet **Audience[!UICONTROL  :]**

   1. Sélectionnez un événement standard tel que **[!UICONTROL Lancé]** et sélectionnez **[!UICONTROL Existe]**.
   1. Sélectionnez un second déclencheur qui est un point de données personnalisé mappé à une variable.
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).

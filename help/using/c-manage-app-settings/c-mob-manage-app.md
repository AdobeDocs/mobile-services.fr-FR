---
description: Vous pouvez suivre et gérer les données que vous recevez de l’application en configurant un ensemble de variables et de mesures.
keywords: mobile
seo-description: Vous pouvez suivre et gérer les données que vous recevez de l’application en configurant un ensemble de variables et de mesures.
seo-title: Gestion de votre application
solution: Experience Cloud,Analytics
title: Gestion de votre application
topic-fix: Metrics
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
exl-id: 599fef94-c188-47f5-b9d6-25a7c8cb07bc
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 100%

---

# Gestion de votre application {#managing-your-app}

Vous pouvez suivre et gérer les données que vous recevez de l’application en configurant un ensemble de variables et de mesures.

## Gestion des variables et des mesures  {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **Variables et mesures standard**

   Chaque application comprend des variables et des mesures pour effectuer le suivi des paniers et des activités d’achat. Certaines informations d’achat ne peuvent être traitées avec des règles de traitement, le SDK expose donc les données contextuelles `"&&products"` spéciales. Par exemple, vous pouvez avoir des variables telles que les ajouts au panier, les suppressions du panier, les passages en caisse, les commandes, etc. Les données contextuelles doivent être mises en correspondance avec les données dans Adobe Analytics. Si cette variable est renseignée par un mappage simple des données contextuelles, il s’agit de la clé qui mappe sur celui-ci. Laissez le champ vide si la variable est renseignée par des règles plus complexes dans les Outils d’administration Analytics.

   Pour de plus amples informations sur les variables et mesures, veuillez consulter :

   * [Variables de produit dans Android](/help/android/analytics-main/products/products.md)
   * [Variables de produit dans iOS](/help/ios/analytics-main/products/products.md)

* **Variables personnalisées**

   La page Variables personnalisées présente toutes les variables Analytics personnalisées configurées pour la suite de rapports contenant les données de votre application. Dans cette page, vous pouvez activer des variables supplémentaires et mapper des données contextuelles sur des variables Analytics.

### Mappage des données contextuelles aux variables Analytics

Cliquez sur **[!UICONTROL Gérer les paramètres de l’application]** > **[!UICONTROL Gérer les variables et mesures]** > **[!UICONTROL Variables personnalisées]**.

Ces mappages appellent le même API utilisé dans les [Règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![Mappage des données contextuelles](assets/custom_data_content.png)

Voici une liste des variables personnalisées que vous pouvez configurer :

* Les **[!UICONTROL Propriétés personnalisées]** (ou props) répondent à la question « laquelle ? » Les props peuvent être définies sur une valeur de texte qui sera associée à d’autres variables et mesures envoyées dans le même accès. Les valeurs peuvent être utilisées pour filtrer les rapports ou peuvent être répertoriées par ordre de classement selon une mesure associée.

   Lorsqu’une valeur est définie pour une propriété dans un appel de suivi (ou accès), elle s’applique uniquement à cet appel.

* Les **[!UICONTROL Variables personnalisées]** (ou eVar) répondent également à la question « laquelle ? ». Toutefois, une valeur d’eVar peut s’appliquer non seulement à l’accès dans lequel elle est envoyée, mais aussi aux variables et mesures envoyées dans les accès consécutifs jusqu’à ce que la valeur expire ou qu’une nouvelle valeur soit définie.
* Les **[!UICONTROL Variables de liste personnalisées (ou variables à valeurs multiples)]** se comportent comme les variables, mais permettent de capturer plusieurs valeurs sur un seul accès. Pour en savoir plus, voir la section [Variables de liste](https://docs.adobe.com/content/help/fr-FR/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html).

Les mappages suivants s’affichent dans Analytics comme ayant été créés dans Mobile Services.

* **[!UICONTROL Nom]**

   Nom convivial de la variable de collecte des données.

* **[!UICONTROL Données contextuelles]**

   Si cette variable est renseignée par un mappage simple des données contextuelles, il s’agit de la clé qui mappe sur celui-ci. Laissez ce champ vide si la variable est renseignée par des règles plus complexes dans les Outils d’administration Analytics.

   Cliquez dans la colonne Données contextuelles et sélectionnez la variable Données contextuelles que vous souhaitez mapper. La liste déroulante contient les variables reçues au cours des 30 derniers jours. Par conséquent, si les données contextuelles que vous souhaitez mapper ne figurent pas dans la liste, vous pouvez les saisir.

* **[!UICONTROL Persistance (Variables personnalisées et Variables de liste personnalisées)]**

   La persistance détermine le point à partir duquel la valeur de la variable personnalisée (eVar) expire ou n’est plus associée à des accès supplémentaires. Si une eVar expire au déclenchement d’un accès, la valeur Aucun sera associée à cet accès pour cette eVar. Cela signifie qu’aucune valeur eVar n’était active lorsque l’accès a été déclenché.

   Vous pouvez sélectionner l’une des options suivantse :

   * **[!UICONTROL Session]**

      La valeur eVar persiste pendant toute la durée de la visite Analytics.

   * **[!UICONTROL Appel de suivi]**

      La valeur eVar persiste uniquement pour l’appel de suivi ou l’accès dans lequel elle était incluse.

   * **[!UICONTROL Ne jamais expirer]**

      La valeur eVar persiste pour tous les appels de suivi ultérieurs.
   * **[!UICONTROL Advanced]**

      Adobe Analytics dispose d’une interface utilisateur avancée pour configurer la persistance des eVar. Si une valeur de persistance est définie pour l’eVar sans qu’elle soit prise en charge dans Mobile Services, cette valeur apparaît dans l’interface utilisateur de Mobile Services.

      Pour gérer les eVar, cliquez sur **[!UICONTROL Gestionnaire de suites de rapports Adobe Analytics]** > **[!UICONTROL Interface utilisateur des variables de conversion]**.

   * **[!UICONTROL Prise en charge des listes]**

      Permet le transfert de plusieurs valeurs à associer à la propriété au cours d’un appel de suivi. Le délimiteur utilisé doit être un caractère et ne peut pas contenir de zéro ni d’espace.

   * **[!UICONTROL Délimiteur]**

      Le délimiteur utilisé doit être un caractère et ne peut pas contenir de zéro ni d’espace.

### Variable Analytics supplémentaires

Vous pouvez activer des variables supplémentaires à l’aide de la liste déroulante située en bas de chaque section de variable.

![ajouter une variable](assets/add_variable.png)

Sélectionnez un numéro de variable inutilisé et saisissez un nom. Vous pouvez éventuellement fournir la variable de données contextuelles que vous souhaitez stocker et toute information supplémentaire.

* **Mesures personnalisées**

   Les mesures (ou événements) répondent aux questions *« combien ? »* ou *« quelle quantité ? »*. Les événements peuvent être incrémentés chaque fois que l’utilisateur effectue une action ou détient des valeurs numériques telles qu’un prix. Les mesures personnalisées incluent des événements tels que la création d’une application, le téléchargement ou l’exportation du fichier PDF ou CSV, l’enregistrement d’une campagne, le téléchargement du SDK, l’exécution d’un rapport, l’ajout d’un lien vers l’App Store, l’activation d’un message intégré à l’application, etc.

   Sélectionnez l’un des types de mesures personnalisées suivants :

   * **[!UICONTROL Nombre entier]**
   * **[!UICONTROL Nombre décimal]**
   * **[!UICONTROL Devise]**

## Gestion des points ciblés {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

Les points ciblés vous permettent de définir des emplacements géographiques que vous pourrez ensuite utiliser à des fins de corrélation dans des rapports, de ciblage avec des messages internes aux applications, etc. Lorsqu’un accès est envoyé dans un point ciblé, celui-ci est rattaché à l’accès en question. Pour plus d’informations sur les points ciblés, voir  [Gestion des points ciblés](/help/using/location/t-manage-points.md).

## Gestion des destinations de lien {#section_F722A387E22A430187B063D358A87711}

Vous pouvez créer, modifier, archiver/ne plus archiver et supprimer des destinations de lien. Ces destinations peuvent alors être invoquées en ligne lors de la création de liens marketing, de notifications push ou de messages in-app. Pour plus d’informations sur les destinations de lien, voir [Gestion des destinations de lien](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md).

## Gestion des postbacks {#section_78B0A8D7AE6940E78D85AE3AB829E860}

Les postbacks permettent d’envoyer les données collectées par Adobe Mobile à un serveur tiers distinct. En mettant à profit les mêmes déclencheurs et caractéristiques que ceux que vous utilisez pour afficher un message in-app, vous pouvez configurer les Mobile pour envoyer des données personnalisées vers une destination tierce. Pour plus d’informations sur les postbacks, voir  [Configuration des postbacks](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md).

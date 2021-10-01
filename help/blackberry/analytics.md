---
description: Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application (veillez à importer ADBMobile.h dans votre classe).
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 13%

---

# Analytics {#analytics}

Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application (veillez à importer ADBMobile.h dans votre classe).

## Activation des rapports sur les applications mobiles dans Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Avant d’ajouter du code, demandez à votre administrateur Analytics de procéder comme suit pour activer le suivi du cycle de vie des applications mobiles. Ces actions permettent de s’assurer que votre suite de rapports est prête à capturer les mesures au démarrage du développement.

1. Ouvrez **[!UICONTROL Outils d’administration]** > **[!UICONTROL Suites de rapports]** et sélectionnez votre ou vos suites de rapports mobiles.
1. Cliquez sur **[!UICONTROL Modifier les paramètres]** > **[!UICONTROL Gestion mobile]** > **[!UICONTROL Rapports d’applications mobiles]**.

   ![Paramètres mobiles](assets/mobile-settings.png)

1. Cliquez sur **[!UICONTROL Activer les derniers rapports d’application]**.

   Vous pouvez également cliquer sur **[!UICONTROL Activer le suivi de l’emplacement mobile]** et **[!UICONTROL Activer les rapports et attribution hérités pour les accès en arrière-plan]**.

   ![Activation du cycle de vie](assets/enable-lifecycle.png)

Les mesures de cycle de vie sont maintenant prêtes à être capturées et les rapports d’applications mobiles apparaissent dans le menu **[!UICONTROL Rapports]** de l’interface des rapports marketing.

## Collecte des mesures de cycle de vie {#task_25D469C62DF84573AEB5E8E950B96205}

1. Pour collecter les mesures de cycle de vie dans votre application, appelez `collectLifecycleData()` dans le constructeur `ApplicationUI`.

   Par exemple :

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Si `collectLifecycleData()` est appelé deux fois au cours de la même session, votre application signale un plantage à chaque appel après le premier. Le SDK définit un indicateur lorsque l’application est arrêtée, indiquant une fermeture réussie. Si cet indicateur n’est pas défini, `collectLifecyleData()` signale un plantage.

## Événements, props et eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

Si vous avez consulté la [référence sur les classes et méthodes ADBMobile](/help/blackberry/methods.md), vous vous demandez probablement où définir des événements, des eVars, des props, des héritiers et des listes. Dans la version 4, vous ne pouvez plus affecter ces types de variables directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application sur les variables Analytics à des fins de reporting.

Les règles de traitement présentent plusieurs avantages :

* Vous pouvez modifier le mapping de vos données sans envoyer de mise à jour à la boutique d’applications.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact. Ces valeurs n’apparaîtront dans les rapports qu’après avoir été mappées à l’aide de règles de traitement.

Toutes les valeurs que vous assignez directement aux variables doivent être ajoutées à la table de hachage `data` HashMap à la place.

## Règles de traitement {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Les règles de traitement sont utilisées pour copier les données que vous envoyez dans des variables de données contextuelles vers des eVars, des props et d’autres variables pour la création de rapports.

[Formation aux règles de traitement](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Règles de traitement](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtention de l’autorisation d’utiliser des règles de traitement](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Nous vous recommandons de regrouper vos variables de données contextuelles à l’aide d’&quot;espaces de noms&quot;, car cela vous aide à conserver un ordre logique. Par exemple, si vous souhaitez collecter des informations sur un produit, vous pouvez définir les variables suivantes :

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement. Les espaces de noms vous permettent donc de voir rapidement les variables qui se trouvent dans le même espace de noms.

En outre, nous avons entendu dire que certains d’entre vous nomment des clés de données contextuelles à l’aide de l’eVar ou du numéro de prop :

```js
"eVar1":"jimbo"
```

Cela peut rendre *légèrement* plus facile lorsque vous effectuez le mappage unique dans les règles de traitement, mais vous perdez la lisibilité pendant le débogage et les futures mises à jour du code peuvent être plus difficiles. Nous vous recommandons plutôt d’utiliser des noms explicites pour les clés et les valeurs :

```js
"username":"jimbo"
```

Les variables contextuelles qui définissent des événements de compteur peuvent avoir la même clé et la même valeur :

```js
"logon":"logon"
```

Les variables de données contextuelles qui définissent les événements d’incrémentation peuvent avoir l’événement comme clé et le montant à incrémenter comme valeur :

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe réserve l’espace de noms « `a.` ». Outre cette petite restriction, les variables de données contextuelles doivent simplement être uniques dans votre société de connexion pour éviter les collisions.

## Activation du suivi hors ligne {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Pour stocker les accès lorsque l’appareil est hors ligne, vous pouvez éventuellement activer le suivi hors ligne dans le fichier `ADBMobileConfig.json` .

Surveillez de très près les exigences d’horodatage décrites dans la référence du fichier de configuration avant d’activer le suivi hors ligne.

## Méthodes Analytics

Pour obtenir la liste des méthodes Analytics disponibles pour BlackBerry, voir *Méthodes Analytics* dans [Adobe de référence pour les classes et méthodes mobiles](/help/blackberry/methods.md).

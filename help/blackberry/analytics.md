---
description: Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application (veillez à importer ADBMobile.h dans votre classe).
seo-description: Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application (veillez à importer ADBMobile.h dans votre classe).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 5%

---


# Analytics {#analytics}

Après avoir ajouté la bibliothèque à votre projet, vous pouvez effectuer n’importe quel appel de méthode Analytics n’importe où dans votre application (veillez à importer ADBMobile.h dans votre classe).

## Activation des rapports d’applications mobiles dans Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Avant d’ajouter du code, demandez à votre administrateur Analytics d’effectuer les opérations suivantes pour activer le suivi du cycle de vie des applications mobiles. Ainsi, votre suite de rapports est prête à capturer les mesures au début du développement.


1. Ouvrez Outils **** d’administration > Suites **[!UICONTROL de]** rapports et sélectionnez votre ou vos suites de rapports mobiles.
1. Cliquez sur **[!UICONTROL Modifier les paramètres]** > Gestion **** mobile > Rapports **[!UICONTROL d’application]** mobile.

   ![](assets/mobile-settings.png)

1. Cliquez sur **[!UICONTROL Activer les derniers rapports]** d’application.

   Vous pouvez également cliquer sur **[!UICONTROL Activer le suivi]** des emplacements mobiles et **[!UICONTROL Activer le Rapports et l’attribution hérités pour les accès]** en arrière-plan.

   ![](assets/enable-lifecycle.png)

Les mesures de cycle de vie sont maintenant prêtes à être capturées et les rapports d’applications mobiles apparaissent dans le menu **[!UICONTROL Rapports]** de l’interface des rapports marketing.

## Collecte de mesures de cycle de vie {#task_25D469C62DF84573AEB5E8E950B96205}

1. Pour collecter les mesures de cycle de vie dans votre application, appelez `collectLifecycleData()` dans le `ApplicationUI` constructeur.

   Par exemple :

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Si `collectLifecycleData()` est appelé deux fois au cours de la même session, votre application signale un blocage à chaque appel après le premier. Le SDK définit un indicateur lorsque l’application est fermée, qui indique une sortie réussie. Si cet indicateur n&#39;est pas défini, `collectLifecyleData()` signale un blocage.

## Événements, props et eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Si vous avez examiné la classe [ADBMobile et la référence](/help/blackberry/methods.md)de méthode, vous vous demandez probablement où définir des événements, des eVars, des props, des héritiers et des listes. Dans la version 4, vous ne pouvez plus affecter ces types de variables directement dans votre application. Au lieu de cela, le SDK utilise des données contextuelles et des règles de traitement pour mapper les données de votre application aux variables Analytics pour le rapports.

Les règles de traitement offrent plusieurs avantages :

* Vous pouvez modifier le mappage de vos données sans envoyer de mise à jour à l’App Store.
* Vous pouvez utiliser des noms significatifs pour les données au lieu de définir des variables spécifiques à une suite de rapports.
* L’envoi de données supplémentaires n’a que peu d’impact. Ces valeurs n’apparaîtront pas dans les rapports tant qu’elles ne seront pas mises en correspondance à l’aide de règles de traitement.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Règles de traitement {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Les règles de traitement permettent de copier les données envoyées dans des variables de données contextuelles vers des variables evar, prop et d’autres variables pour le rapports.

[Formation](https://tv.adobe.com/embed/1181/16506/) sur les règles de traitement au sommet 2013

[Règles de traitement](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtention de l’autorisation d’utiliser des règles de traitement](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Nous vous recommandons de regrouper vos variables de données contextuelles à l’aide d’&quot;espaces de nommage&quot;, car cela vous permet de conserver un ordre logique. Par exemple, si vous souhaitez collecter des informations sur un produit, vous pouvez définir les variables suivantes :

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Les variables de données contextuelles sont triées par ordre alphabétique dans l’interface des règles de traitement. Les espaces de nommage vous permettent donc d’afficher rapidement les variables qui se trouvent dans le même espace de nommage.

En outre, nous avons entendu dire que certains d’entre vous nomment des clés de données contextuelles à l’aide de l’evar ou du numéro prop :

```js
"eVar1":"jimbo"
```

Cela peut rendre la tâche *légèrement* plus facile lorsque vous effectuez le mappage unique dans les règles de traitement, mais vous perdez la lisibilité pendant le débogage et les futures mises à jour du code peuvent s’avérer plus difficiles. Nous vous recommandons plutôt d’utiliser des noms descriptifs pour les clés et les valeurs :

```js
"username":"jimbo"
```

Les variables contextuelles qui définissent des événements de compteur peuvent avoir la même clé et la même valeur :

```js
"logon":"logon"
```

Les variables de données contextuelles qui définissent les événements incrémenteurs peuvent avoir le événement comme clé et le montant à incrémenter comme valeur :

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe réserve l’espace de noms « `a.` ». Outre cette petite restriction, les variables de données contextuelles doivent simplement être uniques dans votre société de connexion pour éviter les collisions.

## Activation du suivi hors ligne {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Pour stocker les accès lorsque le périphérique est hors ligne, vous pouvez également activer le suivi hors ligne dans le `ADBMobileConfig.json` fichier.

Soyez très attentif aux exigences d’horodatage décrites dans la référence de fichier de configuration avant d’activer le suivi hors ligne.

## Méthodes Analytics

Pour une liste des méthodes Analytics disponibles pour BlackBerry, voir Méthodes ** Analytics dans [Adobe Mobile Class et Référence](/help/blackberry/methods.md)des méthodes.
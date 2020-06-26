---
description: Pour commencer à utiliser la solution Experience Cloud Device Co-op, contactez votre représentant Adobe.
seo-description: Pour commencer à utiliser la solution Experience Cloud Device Co-op, contactez votre représentant Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: ht
source-wordcount: '292'
ht-degree: 100%

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Pour commencer à utiliser la solution Experience Cloud Device Co-op, contactez votre représentant Adobe.

Pour activer vos applications mobiles pour la solution Experience Cloud Device Co-op, suivez les étapes ci-après pour les SDK iOS d’Experience Cloud.

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.8.5 ou ultérieure du SDK iOS.

À partir de la version 4.16.1 du SDK, les membres de Device Co-op peuvent exclure leurs données de périphériques mobiles de la solution Experience Cloud Device Co-op. Pour plus d’informations, voir [Configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md) et la méthode `visitorAPI.js` pour [isCoopSafe](https://docs.adobe.com/content/help/fr-FR/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implémentez le SDK Adobe Mobile.

   Pour plus d’informations, voir [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Activez votre Experience Cloud ID.

   Pour plus d’informations, voir [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Transférez les identités authentifiées, par exemple les identifiants de gestion de la relation client ou les courriers électroniques hachés, à l’aide de l’une des méthodes de synchronisation présentées dans ce document.

   Pour plus d’informations, voir [Service Adobe Experience Platform Identity](/help/ios/marketing-cloud/mc-methods.md).

## Indicateur `coopUnsafe`

Voici quelques informations supplémentaires sur l’indicateur `coopUnsafe` :

* Version minimale du SDK : 4.16.1
* Propriété booléenne de l’objet `marketingCloud` qui, lorsqu’elle est définie sur `true`, entraîne l’exclusion du périphérique de la solution Device Co-op d’Experience Cloud.
* La valeur par défaut est `false`.
* Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.

Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste de blocage sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

À noter :

* Si `coopUnsafe` est défini sur `true`, `coop_unsafe=1` sera toujours annexé aux accès Audience Manager et identifiants visiteur.
* Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.



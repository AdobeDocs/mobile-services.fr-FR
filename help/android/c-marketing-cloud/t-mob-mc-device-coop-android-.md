---
description: Pour début à l’aide de l’application Experience Cloud Device Co-op, contactez votre représentant Adobe.
seo-description: Pour début à l’aide de l’application Experience Cloud Device Co-op, contactez votre représentant Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Pour début à l’aide de l’application Experience Cloud Device Co-op, contactez votre représentant Adobe.

Pour activer vos applications mobiles pour Experience Cloud Device Co-op, procédez comme suit pour les SDK Android Experience Cloud :

>[!IMPORTANT]
>
>Le SDK Android version 4.8.3 ou ultérieure est requis pour cette fonctionnalité.

À partir de la version 4.16.1 du SDK, les membres Device Co-op peuvent exclure leurs données de périphériques mobiles de la version Experience Cloud Device Co-op. Pour plus d’informations, voir Configuration [JSON](/help/android/configuration/json-config/json-config.md) ADBMobile et la `visitorAPI.js` méthode pour [isCoopSafe](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implémentez le SDK Adobe Mobile.

   Pour plus d’informations, voir [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).
1. Activez votre Experience Cloud ID.

   Pour plus d’informations, voir [Service d’Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).
1. Transférez les identités authentifiées, par exemple les identifiants de gestion de la relation client ou les courriers électroniques hachés, à l’aide de l’une des méthodes de synchronisation.

   Pour plus d’informations, voir [Service Adobe Experience Platform Identity](/help/android/c-marketing-cloud/mc-methods.md).

## Indicateur `coopUnsafe`

Voici quelques informations supplémentaires sur l’indicateur `coopUnsafe` :

* Version minimale du SDK : 4.16.1
* Propriété booléenne de l’objet `marketingCloud` qui, lorsqu’elle est définie sur `true`, entraîne l’exclusion du périphérique de la solution Device Co-op d’Experience Cloud.
* La valeur par défaut est `false`.
* Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.

Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste noire sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

À noter :

* Si `coopUnsafe` est défini sur `coop_unsafe=1``true`, sera toujours annexé aux accès Audience Manager et identifiants visiteur.
* Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.
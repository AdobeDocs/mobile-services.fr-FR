---
description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.

Afin d’activer les applications mobiles destinées à Experience Cloud Device Co-op, procédez comme suit pour les SDK iOS Experience Cloud :

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.8.5 ou ultérieure du SDK iOS.

À partir de la version 4.16.1 du SDK, les membres de Device Co-op peuvent exclure les données de leur appareil mobile de la solution Device Co-op d’Experience Cloud. Pour plus d’informations, voir [Fichier de configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md) et la méthode `visitorAPI.js` pour [isCoopSafe](https://marketing.adobe.com/resources/help/fr_FR/mcvid/mcvid-coopsafe.html).

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

Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste noire sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

À noter :

* Si `coopUnsafe` est défini sur `coop_unsafe=1``true`, sera toujours annexé aux accès Audience Manager et identifiants visiteur.
* Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.



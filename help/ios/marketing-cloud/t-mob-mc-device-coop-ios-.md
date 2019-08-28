---
description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434 a 6 f 8 f-ec 24-439 d -95 f 0-a 246 b 384 b 3 b 5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.

Afin d’activer les applications mobiles destinées à Experience Cloud Device Co-op, procédez comme suit pour les SDK iOS Experience Cloud :

>[!IMPORTANT]
>
>Cette fonctionnalité requiert le SDK ios version 4.8.5 ou ultérieure.

À partir de la version 4.16.1 du SDK, les membres de Device Co-op peuvent exclure les données de leur appareil mobile de la solution Device Co-op d’Experience Cloud. Pour plus d’informations, voir [Fichier de configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md) et la méthode `visitorAPI.js` pour [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implémentez le SDK Adobe Mobile.

   Pour plus d'informations, voir [Mise en œuvre principale et Cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Activez votre Experience Cloud ID.

   Pour plus d’informations, voir [ d’Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Transférez les identités authentifiées, par exemple les identifiants de gestion de la relation client ou les courriers électroniques hachés, à l’aide de l’une des méthodes de synchronisation présentées dans ce document.

   Pour plus d'informations, voir [Méthodes du service d'identité Adobe Experience Platform](/help/ios/marketing-cloud/mc-methods.md).

## `coopUnsafe` indicateur

Here is some additional information on the `coopUnsafe` flag:

* Version minimale du SDK : 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Default value is `false`.
* Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.

Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste noire sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

À noter :

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Si vous activez le transfert côté serveur Analytics vers Audience Manager, `coop_unsafe=1` sera également annexé aux accès Analytics.



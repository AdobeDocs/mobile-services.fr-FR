---
description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-description: Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7 bb 8 a 19 c -4 b 80-4911-879 d-f 9941 baa 3 b 62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Contactez votre représentant Adobe pour commencer à utiliser Experience Cloud Device Co-op.

Afin d’activer les applications mobiles destinées à Experience Cloud Device Co-op, procédez comme suit pour les SDK Android Experience Cloud :

>[!IMPORTANT]
>
>Cette fonctionnalité requiert le SDK Android version 4.8.3 ou ultérieure.

À partir de la version 4.16.1 du SDK, les membres de Device Co-op peuvent exclure les données de leur appareil mobile de la solution Device Co-op d’Experience Cloud. Pour plus d’informations, voir [Fichier de configuration JSON ADBMobile](/help/android/configuration/json-config/json-config.md) et la méthode `visitorAPI.js` pour [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implémentez le SDK Adobe Mobile.

   Pour plus d'informations, voir [Mise en œuvre principale et Cycle de vie](/help/android/getting-started/dev-qs.md).
1. Activez votre Experience Cloud ID.

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. Transférez les identités authentifiées, par exemple les identifiants de gestion de la relation client ou les courriers électroniques hachés, à l’aide de l’une des méthodes de synchronisation.

   Pour plus d'informations, voir [Méthodes du service d'identité Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md).

## `coopUnsafe` indicateur

Voici quelques informations supplémentaires sur l’indicateur `coopUnsafe` :

* Version minimale du SDK : 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Default value is `false`.
* Ce paramètre est utilisé **uniquement** pour les clients configurés pour Device Co-op.

Pour les membres de Device Co-op ayant besoin de cette valeur définie sur `true`, vous devez travailler avec l’équipe Device Co-op afin de demander un drapeau de liste noire sur votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

À noter :

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.
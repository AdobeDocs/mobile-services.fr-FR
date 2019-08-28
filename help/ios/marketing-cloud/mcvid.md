---
description: Le service d'identité Adobe Experience Platform fournit un identifiant visiteur universel dans les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-description: Le service d'identité Adobe Experience Platform fournit un identifiant visiteur universel dans les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Experience Cloud ID
topic: Développeur et mise en œuvre
uuid: 13628 ea 8-3 cd 4-4 cfc -8 ff 6-722 c 33 f 7813 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Le service d'identité Adobe Experience Platform fournit un identifiant visiteur universel dans les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.

>[!TIP]
>
>Vous n'avez pas besoin de renseigner l'identifiant d'expérience, sauf si vous utilisez le service d'identité Adobe Experience Platform. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**La version 4.3 ou ultérieure du SDK est requise.**

## Activation de l'ID d'expérience {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [l'implémentation principale et le cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vérifiez que `ADBMobileConfig.json` les fichiers contiennent `marketingCloud``org`les éléments suivants :

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >You must include `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Pour plus d'informations, voir [Configuration JSON adbmobile](/help/ios/getting-started/requirements.md).

Une fois la configuration terminée, un Experience Cloud ID est généré et inclus sur tous les accès. D’autres identifiants visiteur, comme les identifiants personnalisés et générés automatiquement, continueront à être envoyés avec chaque accès.

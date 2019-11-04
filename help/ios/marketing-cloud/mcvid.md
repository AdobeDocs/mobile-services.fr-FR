---
description: Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-description: Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic: Développeur et mise en œuvre
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.

>[!TIP]
>
>Il n’est pas nécessaire de renseigner l’Experience Cloud ID, sauf si vous utilisez le service d’identification Adobe Experience Platform. Pour plus d’informations, voir [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/fr_FR/mcvid/).

**La version 4.3 ou ultérieure du SDK est requise.**

## Activez votre Experience Cloud ID.{#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* dans [Mise en œuvre principale et cycle de vie](/help/ios/getting-started/dev-qs.md).
1. Importez la bibliothèque :

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vérifiez que les fichiers `ADBMobileConfig.json` contiennent les éléments `marketingCloud` `org` :

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Les identifiants d’organisation d’Experience Cloud identifient de manière unique chaque entreprise cliente dans Adobe Experience Cloud et ressemblent à ceci : `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Vous devez inclure `@AdobeOrg`.

   Si ces valeurs ne sont pas présentes, téléchargez un fichier `ADBMobileConfig.json` mis à jour depuis Adobe Mobile Services. Pour plus d’informations, voir [Configuration JSON ADBMobile](/help/ios/getting-started/requirements.md).

Une fois la configuration terminée, un Experience Cloud ID est généré et inclus sur tous les accès. D’autres identifiants visiteur, comme les identifiants personnalisés et générés automatiquement, continueront à être envoyés avec chaque accès.

---
description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-description: Le service d’identité Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-title: Experience Cloud ID configuration
solution: Marketing Cloud,Analytics
title: Experience Cloud ID configuration
topic: Développeur et mise en œuvre
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.

>[!TIP]
>
>Vous n’avez pas besoin de renseigner cet ID, sauf si vous utilisez le service d’identité Adobe Experience Platform. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>This functionality requires SDK version 4.3 or later.

Pour activer l’Experience Cloud ID, procédez comme suit :

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration à votre projet* IntelliJ IDEA ou Eclipse dans l’implémentation et le cycle de vie [](/help/android/getting-started/dev-qs.md)principaux.

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Vérifiez que le `ADBMobileConfig.json` fichier contient le `marketingCloudorg`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Les ID d’organisation d’Experience Cloud identifient de manière unique chaque entreprise cliente dans Adobe Experience Cloud ; ils ressemblent à la valeur suivante :

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >You must include `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Pour obtenir plus d’informations, voir [Avant de commencer](/help/android/getting-started/requirements.md).

Une fois la configuration terminée, un Experience Cloud ID est généré et inclus sur tous les accès. D’autres identifiants, tels que les identifiants personnalisés et générés automatiquement, continuent à être envoyés avec chaque accès.

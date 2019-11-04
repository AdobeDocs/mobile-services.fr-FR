---
description: Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-description: Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.
seo-title: Configuration de l’Experience Cloud ID
solution: Experience Cloud,Analytics
title: Configuration de l’Experience Cloud ID
topic: Développeur et mise en œuvre
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration de l’Experience Cloud ID {#experience-cloud-id-configuration}

Le service d’identification Adobe Experience Platform fournit un identifiant visiteur universel pour toutes les solutions Experience Cloud. Il est requis par Analytics pour Target, la pulsation vidéo et les futures intégrations d’Experience Cloud.

>[!TIP]
>
>Il n’est pas nécessaire de renseigner cet ID, sauf si vous utilisez le service d’identification Adobe Experience Platform. Pour plus d’informations, voir [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/fr_FR/mcvid/).

>[!IMPORTANT]
>
>Pour utiliser cette fonctionnalité, vous devez disposer de la version 4.3 ou ultérieure du SDK

Pour activer l’Experience Cloud ID, procédez comme suit :

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration au projet IntelliJ IDEA ou Eclipse* dans [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Vérifiez que le fichier `ADBMobileConfig.json` contient le `marketingCloudorg` :

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
   >Vous devez inclure `@AdobeOrg`.

   Si ces ID ne sont pas configurés, téléchargez un fichier `ADBMobileConfig.json` mis à jour depuis Adobe Mobile Services. Pour obtenir plus d’informations, voir [Avant de commencer](/help/android/getting-started/requirements.md).

Une fois la configuration terminée, un Experience Cloud ID est généré et inclus sur tous les accès. D’autres identifiants, tels que les identifiants personnalisés et générés automatiquement, continuent à être envoyés avec chaque accès.

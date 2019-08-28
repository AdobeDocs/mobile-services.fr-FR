---
description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-title: Définition de l’état de souscription de l’utilisateur
solution: Marketing Cloud, Analytics
title: Définition de l’état de souscription de l’utilisateur
topic: Développeur et mise en œuvre
uuid: 44 a 09 a 25-93 c 6-4 e 1 a-b 69 e -710018 e 8 b 6 c 3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Vous pouvez décider si l’activité d’Analytics, de Target et d’Audience Manager est autorisée sur un périphérique en utilisant les paramètres suivants :

* `privacyDefault` dans [la configuration JSON adbmobile](/help/ios/configuration/json-config/json-config.md).

   Ce paramètre contrôle le paramètre initial qui persiste jusqu’à ce qu’il soit modifié dans le code.

* `setPrivacyStatus` method.

   Une fois le paramètre de confidentialité modifié à l’aide de cette méthode, la modification est permanente jusqu’à ce qu’il soit changé à nouveau à l’aide de cette méthode ou jusqu’au moment où vous désinstallez et réinstallez l’application.

   Pour obtenir plus d’informations sur les méthodes, voir [Méthodes de configuration](/help/ios/configuration/json-config/json-config.md).

Vous trouverez ci-dessous des informations sur chaque état de confidentialité :

* **Inclusion**

   * Analytics : les accès sont envoyés.
   * Target : les demandes de mbox sont envoyées.
   * Audience Manager : les signaux et la synchronisation des identifiants sont envoyés.
   * Value in the JSON config file: `optedin`
   * Valeur dans `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Exclusion**

   * Analytics : les accès sont ignorés.
   * Target : les demandes de mbox ne sont pas autorisées.
   * Audience Manager : les signaux et la synchronisation des identifiants ne sont pas autorisés.
   * Value in the JSON config file: `optedout`
   * Valeur dans `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Inconnu**

   * Analytics : Si le suivi hors ligne **est** activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).

      Si le suivi hors ligne **n’est pas** activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.

   * Target : les demandes de mbox sont envoyées.
   * Audience Manager : les signaux et la synchronisation des identifiants sont envoyés.
   * Value in the JSON config file: `optunknown`
   * Valeur dans `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Exemples {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```


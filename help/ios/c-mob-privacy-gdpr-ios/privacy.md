---
description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-title: Définition de l’état de souscription de l’utilisateur
solution: Experience Cloud,Analytics
title: Définition de l’état de souscription de l’utilisateur
topic: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Définition de l’état de souscription de l’utilisateur {#setting-the-user-s-opt-status}

Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.

>[!IMPORTANT]
>
>À compter des SDK Experience Cloud pour iOS version 4.15, la définition de l’état de confidentialité sur `unknown` inclut les accès Audience Manager ID et Experience Cloud ID.

Vous pouvez décider si l’activité d’Analytics, de Target et d’Audience Manager est autorisée sur un périphérique en utilisant les paramètres suivants :

* `privacyDefault` dans la [configuration JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

   Ce paramètre contrôle le paramètre initial qui persiste jusqu’à ce qu’il soit modifié dans le code.

* `setPrivacyStatus` method.

   Une fois le paramètre de confidentialité modifié à l’aide de cette méthode, la modification est permanente jusqu’à ce qu’il soit changé à nouveau à l’aide de cette méthode ou jusqu’au moment où vous désinstallez et réinstallez l’application.

   Pour obtenir plus d’informations sur les méthodes, voir  [Méthodes de configuration](/help/ios/configuration/json-config/json-config.md).

Voici des informations sur chaque état de confidentialité :

* **Inclusion**

   * Analytics : les accès sont envoyés.
   * Target : les demandes de mbox sont envoyées.
   * Audience Manager : les signaux et la synchronisation des identifiants sont envoyés.
   * Valeur dans le fichier JSON Config : `optedin`
   * Valeur dans `setPrivacyStatus` : `ADBMobilePrivacyStatusOptIn`

* **Exclusion**

   * Analytics : les accès sont ignorés.
   * Target : les demandes de mbox ne sont pas autorisées.
   * Audience Manager : les signaux et la synchronisation des identifiants ne sont pas autorisés.
   * Valeur dans le fichier JSON Config : `optedout`
   * Valeur dans `setPrivacyStatus` : `ADBMobilePrivacyStatusOptOut`

* **Inconnu**

   * Analytics : Si le suivi hors ligne **est** activé, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).

      Si le suivi hors ligne **n’est pas** activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.

   * Target : les demandes de mbox sont envoyées.
   * Audience Manager : les signaux et la synchronisation des identifiants sont envoyés.
   * Valeur dans le fichier JSON Config : `optunknown`
   * Valeur dans `setPrivacyStatus` : `ADBMobilePrivacyStatusUnknown`

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


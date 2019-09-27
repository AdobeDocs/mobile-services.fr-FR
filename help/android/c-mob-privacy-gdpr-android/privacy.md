---
description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-title: Définition de l’état d’acceptation de l’utilisateur
solution: Marketing Cloud,Analytics
title: Définition de l’état d’acceptation de l’utilisateur
topic: Développeur et mise en œuvre
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Vous pouvez contrôler si l’activité d’Analytics, de Target et d’Audience Manager est autorisée sur un appareil à l’aide des paramètres suivants :

* `privacyDefault` in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

   Ce paramètre contrôle le paramètre initial qui persiste jusqu’à ce qu’il soit modifié dans le code.

* The `Config.setPrivacyStatus` method.

   Une fois que le paramètre de confidentialité est modifié à l’aide de cette méthode, cette modification reste en vigueur jusqu’à la prochaine modification ou jusqu’à la désinstallation et la réinstallation de l’application. Pour obtenir plus d’informations sur les méthodes, voir [Méthodes de configuration](/help/android/configuration/methods.md).

Le tableau suivant décrit chaque état de confidentialité :

* **Inclusion**

   * **Analytics** : les accès sont envoyés.
   * **Target** : les demandes de mbox sont envoyées.
   * **Audience Manager** : les signaux et la synchronisation des identifiants sont envoyés.
   * Value in the JSON Config file: `optedin`
   * Value in : `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_IN`

* **Exclusion**

   * **Analytics** : les accès sont ignorés.
   * **Target** : les demandes de mbox ne sont pas autorisées.
   * **Audience Manager** : les signaux et la synchronisation des identifiants ne sont pas autorisés.
   * Value in the JSON config file: `optedout`
   * Value in : `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Unknown (Inconnu)**

   * **Analytics**: If offline tracking **enabled**, hits are saved until the privacy status changes to opt-in (hits are sent) or opt-out (hits are discarded).

      Si le suivi hors ligne <b>n’est pas</b> activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.
   * **Target** : les demandes de mbox sont envoyées.
   * **Audience Manager** : les signaux et la synchronisation des identifiants sont envoyés.
   * Value in the JSON config file: `optunknown`
   * Valeur dans `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## Exemples {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```


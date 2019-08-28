---
description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-title: Définition de l'état d'acceptation de l'utilisateur
solution: Marketing Cloud, Analytics
title: Définition de l'état d'acceptation de l'utilisateur
topic: Développeur et mise en œuvre
uuid: f 8 a 3 e 6 be -44 dd -494 e -9 cda-dbbac 86 d 6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Vous pouvez contrôler si l’activité d’Analytics, de Target et d’Audience Manager est autorisée sur un appareil à l’aide des paramètres suivants :

* `privacyDefault` dans [la configuration JSON adbmobile](/help/android/configuration/json-config/json-config.md).

   Ce paramètre contrôle le paramètre initial qui persiste jusqu’à ce qu’il soit modifié dans le code.

* `Config.setPrivacyStatus` Méthode.

   Une fois que le paramètre de confidentialité est modifié à l’aide de cette méthode, cette modification reste en vigueur jusqu’à la prochaine modification ou jusqu’à la désinstallation et la réinstallation de l’application. Pour obtenir plus d’informations sur les méthodes, voir [Méthodes de configuration](/help/android/configuration/methods.md).

Le tableau suivant décrit chaque état de confidentialité :

* **Inclusion**

   * **Analytics** : les accès sont envoyés.
   * **Target** : les demandes de mbox sont envoyées.
   * **Audience Manager** : les signaux et la synchronisation des identifiants sont envoyés.
   * Value in the JSON Config file: `optedin`
   * Valeur dans `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Exclusion**

   * **Analytics** : les accès sont ignorés.
   * **Target** : les demandes de mbox ne sont pas autorisées.
   * **Audience Manager** : les signaux et la synchronisation des identifiants ne sont pas autorisés.
   * Value in the JSON config file: `optedout`
   * Valeur dans `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Inconnu**

   * **Analytics**: Si le suivi hors ligne **est activé**, les accès sont enregistrés jusqu'à ce que l'état de confidentialité soit remplacé (accès envoyé) ou exclusion (les accès sont ignorés).

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


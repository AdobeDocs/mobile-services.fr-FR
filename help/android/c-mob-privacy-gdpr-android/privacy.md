---
description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-description: Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.
seo-title: Définition de l’état de souscription de l’utilisateur
solution: Experience Cloud,Analytics
title: Définition de l’état de souscription de l’utilisateur
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 81%

---


# Définition de l’état de souscription de l’utilisateur{#setting-the-user-s-opt-status}

Consultez ces informations en cas de demande de suppression de données en vertu du RGPD.

>[!IMPORTANT]
>
>À partir de la version 4.15 du SDK Android, la définition de l’état de confidentialité sur `unknown` inclut les accès Audience Manager ID et Experience Cloud ID.

Vous pouvez contrôler si l’activité d’Analytics, de Target et d’Audience Manager est autorisée sur un appareil à l’aide des paramètres suivants :

* `privacyDefault` dans la [configuration JSON ADBMobile](/help/android/configuration/json-config/json-config.md).

   Ce paramètre contrôle le paramètre initial qui persiste jusqu’à ce qu’il soit modifié dans le code.

* La méthode `Config.setPrivacyStatus`.

   Une fois que le paramètre de confidentialité est modifié à l’aide de cette méthode, cette modification reste en vigueur jusqu’à la prochaine modification ou jusqu’à la désinstallation et la réinstallation de l’application. Pour obtenir plus d’informations sur les méthodes, voir [Méthodes de configuration](/help/android/configuration/methods.md).

Le tableau suivant décrit chaque état de confidentialité :

* **Inclusion**

   * **Analytics**: Les accès sont envoyés.
   * **Cible**: Les requêtes de mbox sont envoyées.
   * **audience manager**: Les signaux et les synchronisations d’identifiants sont envoyés.
   * Valeur dans le fichier JSON Config : `optedin`
   * Valeur dans `setPrivacyStatus` : `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Exclusion**

   * **Analytics**: Les accès sont ignorés.
   * **Cible**: Les requêtes de mbox ne sont pas autorisées.
   * **audience manager**: Les signaux et les synchronisations d’ID ne sont pas autorisés.
   * Valeur dans le fichier JSON Config : `optedout`
   * Valeur dans `setPrivacyStatus` : `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Inconnu**

   * **Analytics** : Si le suivi hors ligne est **activé**, les accès sont enregistrés jusqu’à ce que l’état de confidentialité soit défini sur inclusion (les accès sont envoyés) ou sur exclusion (les accès sont ignorés).

      Si le suivi hors ligne <b>n’est pas</b> activé, les accès sont ignorés jusqu’à ce que l’état de confidentialité soit défini sur inclusion.
   * **Cible**: Les requêtes de mbox sont envoyées.
   * **audience manager**: Les signaux et les synchronisations d’identifiants sont envoyés.
   * Valeur dans le fichier JSON Config : `optunknown`
   * Valeur dans `setPrivacyStatus` : `MOBILE_PRIVACY_STATUS_UNKNOWN`

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


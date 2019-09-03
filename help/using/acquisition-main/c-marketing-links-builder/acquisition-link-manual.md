---
description: Vous pouvez créer des liens marketing pour acquérir instantanément de nouveaux utilisateurs d'applications mobiles en configurant manuellement les paramètres d'URL.
keywords: mobile
seo-description: Vous pouvez créer des liens marketing pour acquérir instantanément de nouveaux utilisateurs d'applications mobiles en configurant manuellement les paramètres d'URL.
seo-title: Création manuelle de liens d'acquisition
solution: Marketing Cloud, Analytics
title: Création manuelle de liens d'acquisition
topic: Mesures
uuid: d 7709203-f 793-4982-adaa -9 c 3 c 914 aca 2 b
translation-type: tm+mt
source-git-commit: 54e3b2d673356a616987537d20758bef8b044db4

---


# Création manuelle de liens d'acquisition {#create-acquisition-link-manually}

Vous pouvez créer des liens marketing pour acquérir instantanément de nouveaux utilisateurs d'applications mobiles en configurant manuellement les paramètres d'URL.

>[!IMPORTANT]
>
>Cette fonctionnalité requiert le SDK version 4.6 ou ultérieure. Pour plus d'informations, voir [Conditions préalables à l'acquisition](/help/using/acquisition-main/c-acquisition-prerequisites.md).

Le diagramme suivant illustre les composants d'un lien de suivi créé manuellement et affiche les différents paramètres d'URL que vous devez configurer correctement lors de la création manuelle de liens d'acquisition.

![](assets/acquisition_url.png)

Ce lien est configuré en vue d’exécuter une redirection spécifique à la plateforme vers la boutique Google Play ou l’App Store d’Apple pour une application mobile. Si la destination ne peut pas être déterminée, la boutique est par défaut configurée sur l’App Store d’Apple. Une fois l’application installée, la clé contextuelle personnalisée `my.custom.key:test` est jointe à l’accès à l’installation d’Analytics.

Pour créer des liens manuellement, utilisez le format d’URL suivant :

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>La version du SDK Android que vous utilisez n'a aucun impact sur ce processus.

Assurez-vous d’utiliser le bon protocole pour les appareils iOS :

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** if you are using iOS SDK 4.7.0 or later and **[!UICONTROL Use HTTPS]** **is** selected on the Manage App Settings page.

Les conditions suivantes ont été respectées :

* `{mobile-services-app-hash}` correspond à l'identifiant d'application dans `acquisition:appid ` le fichier de configuration.

   You can locate `{mobile-services-app-hash}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` est une liste de paramètres de requête d'URL spécifiquement nommés.

Voici la liste des paramètres :

* **`a_g_id`**

   Identifiant d’application dans le Google Play Store.

   * Exemple de valeur : `com.adobe.beardcons`

* **`a_g_lo`**

   Remplacement de l’environnement local du Google Play Store.

   * Exemple de valeur : `ko`

* **`a_i_id`**

   Identifiant d’application iTunes.

   * Exemple de valeur : `835196493`

* **`a_i_lo`**

   Remplacement de l’environnement local iTunes.

   * Exemple de valeur : `jp`

* **`a_dd`**

   Boutique par défaut pour la redirection automatique.

   * Exemple de valeur : `i | g`

* **`a_cid`**

   Remplacement d’identifiant personnalisé (généralement IDFA pour iOS ou ADID pour Android).

   * Exemple de valeur : `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * Exemple de valeur : `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   Nom de la campagne d’acquisition.

   Ce paramètre est indispensable à la génération de rapports lorsque vous souhaitez comparer les performances de différents liens d’acquisition.

   * Exemple de valeur : Conférence Summit 2015

* **`ctxa.referrer.campaign.trackingcode`**

   Code de suivi

   Ce paramètre est indispensable à la génération de rapports lorsque vous souhaitez comparer les performances de différents liens d’acquisition.

   * Exemple de valeur : `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   Source.

   * Exemple de valeur : Réseau publicitaire

* **`ctxa.referrer.campaign.medium`**

   Méthode

   * Exemple de valeur : Courriel

* **`ctxa.referrer.campaign.content`**

   Contenu

   * Exemple de valeur : Image n ° 325689

* **`ctxa.referrer.campaign.term`**

   Terme

   * Exemple de valeur : randonnée + bottes


Lorsque vous créez manuellement des liens d'acquisition, tenez compte des informations suivantes :

* Tous les paramètres qui ne correspondent pas à ceux du tableau sont transmis lors de la redirection vers la boutique d’applications.
* Tous les paramètres sont techniquement facultatifs, bien que le lien ne soit pas fonctionnel, si au moins un identifiant de magasin est spécifié.

   An example of a store ID is `a_g_id`/ `a_i_id`.

* Si la boutique de destination ne peut être déterminée de façon automatique, et qu’aucune boutique n’est définie par défaut, le lien renvoie une erreur 404.


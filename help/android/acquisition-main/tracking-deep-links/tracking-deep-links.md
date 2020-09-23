---
description: Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.
keywords: android;library;mobile;sdk
seo-description: Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.
seo-title: Suivi des liens profonds dans Adobe Mobile Services
solution: Experience Cloud,Analytics
title: Suivi des liens profonds
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 100%

---


# Suivi des liens profonds {#tracking-deep-links}

Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.

## Suivi des liens profonds

1. Ajoutez le SDK à votre projet et mettez en œuvre les mesures de cycle de vie.

   Pour plus d’informations, voir *Ajout du SDK et du fichier de configuration au projet IntelliJ IDEA ou Eclipse* dans [Mise en œuvre principale et cycle de vie](/help/android/getting-started/dev-qs.md).

1. Enregistrez l’application pour permettre le traitement des URL.

   Pour en savoir plus, consultez la rubrique [URL](https://developer.android.com/training/basics/intents/filters.html).
1. Transmettez l’activité avec l’intention de lien profond au SDK Adobe à l’aide de `collectLifecycleData`.

   Voici un exemple de suivi de lien profond :

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

Le SDK Adobe Mobile peut analyser les paires clé-valeur de données ajoutées à n’importe quel lien profond ou universel, à condition que le lien contienne une clé comportant une étiquette `a.deeplink.id` et une valeur correspondante non nulle générée par l’utilisateur. Toutes les paires clé-valeur de données ajoutées au lien seront analysées, associées à un accès de cycle de vie et envoyées à Adobe Analytics, à condition que le lien contienne la clé et la valeur `a.deeplink.id`.

Vous pouvez également ajouter une ou plusieurs des clés réservées suivantes (avec les valeurs générées par l’utilisateur) au lien profond ou universel :

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Ces clés sont des variables prémappées pour la création de rapports dans Adobe Analytics. Pour obtenir plus d’informations sur le mappage et les règles de traitement, voir [Règles de traitement et données contextuelles](https://docs.adobe.com/content/help/fr-FR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Suivi de liens profonds différés (pour utilisation avec les liens marketing)

Dans le cas d’un lien profond différé, le SDK Adobe ouvre une nouvelle intention avec le lien profond comme données d’intention. Ce processus est traité comme un lien profond externe à l’aide du code ci-dessus.

## Informations publiques sur les liens profonds {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```


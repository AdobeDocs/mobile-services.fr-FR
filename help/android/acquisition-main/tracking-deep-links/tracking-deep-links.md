---
description: Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.
keywords: android ; library ; mobile ; sdk
seo-description: Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.
seo-title: Suivi des liens profonds dans Adobe Mobile Services
solution: Marketing Cloud, Analytics
title: Suivi des liens profonds
topic: Développeur et mise en œuvre
uuid: ebb 1 c 08 c-a 246-40 b 3-9 ac 6-4606 a 14 b 4 c 5 a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

Utilisez ces informations pour effectuer le suivi des liens profonds et des liens profonds différés dans vos applications mobiles à l’aide du SDK Android pour Adobe Mobile.

## Suivi des liens profonds

1. Ajoutez le SDK à votre projet et mettez en œuvre les mesures de cycle de vie.

   Pour plus d’informations, voir *Ajoutez le SDK et le fichier Config à votre projet intellij IDEA ou Eclipse* dans [l'implémentation principale et le cycle de vie](/help/android/getting-started/dev-qs.md).

1. Enregistrez l’application pour permettre le traitement des URL.

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

En outre, vous pouvez ajouter une ou plusieurs des clés réservées suivantes (avec les valeurs générées par l'utilisateur) au lien profond ou universel :

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Ces clés sont des variables prémappées pour la création de rapports dans Adobe Analytics. Pour obtenir plus d’informations sur le mappage et les règles de traitement, voir [Règles de traitement et données contextuelles](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Suivi des liens profonds différés (pour une utilisation avec les liens marketing)

Dans le cas d’un lien profond différé, le SDK Adobe ouvre une nouvelle intention avec le lien profond comme données d’intention. Ce processus est traité comme un lien profond externe à l’aide du code ci-dessus.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```


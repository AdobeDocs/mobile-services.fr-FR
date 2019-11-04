---
description: Vous pouvez utiliser ces informations pour vous aider à comprendre les postbacks et leur fonctionnement.
keywords: android;library;mobile;sdk
seo-description: Vous pouvez utiliser ces informations pour vous aider à comprendre les postbacks et leur fonctionnement.
seo-title: Exemple de postback
solution: Experience Cloud,Analytics
title: Exemple de postback
topic: Développeur et mise en œuvre
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Exemple de postback{#postbacks-example}

Vous pouvez utiliser ces informations pour vous aider à comprendre les postbacks et leur fonctionnement.

>[!CAUTION]
>
>Cet exemple est fourni à titre d’information uniquement. Le fichier `ADBMobileConfig.json` doit être configuré dans l’interface utilisateur Adobe Mobile et ne doit pas être modifié manuellement. En effet, un fichier de configuration modifié manuellement peut s’avérer problématique lorsque la configuration des messages à distance est activée.

## `ADBMobileConfig.json` définition {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Exemple de code {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Comme son état est `“MainMenu”`, cet appel de suivi déclenche le message de postback ci-dessus. L’URL remplacera toutes les variables du modèle par les valeurs issues de l’accès. En présumant que la session précédente de l’utilisateur a duré 132 secondes et que ce dernier utilise le SDK Android version 4.6.0, l’URL résultante ressemble à :

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`

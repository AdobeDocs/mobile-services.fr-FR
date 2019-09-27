---
description: Exemples de définitions et de codes source pour la fonctionnalité des postbacks.
seo-description: Exemples de définitions et de codes source pour la fonctionnalité des postbacks.
seo-title: Exemple de postback
solution: Marketing Cloud,Analytics
title: Exemple de postback
topic: Développeur et mise en œuvre
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

Exemples de définitions et de codes source pour la fonctionnalité des postbacks.

>[!CAUTION]
>
>Cet exemple est fourni à titre d’information uniquement. Le fichier `ADBMobileConfig.json` doit être configuré dans l’interface utilisateur Adobe Mobile et ne doit pas être modifié manuellement. En effet, un fichier de configuration modifié manuellement peut s’avérer problématique lorsque la configuration des messages à distance est activée.

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. L’URL remplace toutes les variables de modèle par les valeurs de l’accès. En supposant que la session précédente de l’utilisateur ait duré 132 secondes et qu’il se trouve sur le SDK iOS version 4.6.0, voici un exemple de l’URL qui en résulte :

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`

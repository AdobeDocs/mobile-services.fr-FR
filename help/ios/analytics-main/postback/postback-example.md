---
description: Exemples de définitions et de codes source pour la fonctionnalité des postbacks.
solution: Experience Cloud Services,Analytics
title: Exemple de postback
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# Exemple de postback {#postback-example}

Exemples de définitions et de codes source pour la fonctionnalité des postbacks.

>[!CAUTION]
>
>Cet exemple est fourni à titre d’information uniquement. Le fichier `ADBMobileConfig.json` doit être configuré dans l’interface utilisateur Adobe Mobile et ne doit pas être modifié manuellement. En effet, un fichier de configuration modifié manuellement peut s’avérer problématique lorsque la configuration des messages à distance est activée.

## Définition du fichier ADBMobileConfig.json {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Exemple de code {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Comme son état est `"MainMenu"`, cet appel de suivi déclenche le message de postback ci-dessus. L’URL remplace toutes les variables du modèle par les valeurs issues de l’accès. En supposant que la session précédente de l’utilisateur a duré 132 secondes et que l’utilisateur utilise une version 4.6.0 du SDK iOS, voici un exemple de l’URL résultante :

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`

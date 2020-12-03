---
description: 'null'
seo-description: 'null'
seo-title: Démarrage rapide pour les développeurs
solution: Experience Cloud,Analytics
title: Démarrage rapide pour les développeurs
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# Démarrage rapide pour les développeurs{#developer-quick-start}

Voici quelques informations sur la mise en oeuvre de la bibliothèque de plateformes Windows universelles.

>[!IMPORTANT]
>
>Pour mettre en oeuvre le SDK, vous devez disposer de Visual Studio 2013 ou version ultérieure.

## Obtention du kit SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le fichier de téléchargement [du](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) SDK, vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plate-forme prise en charge. Vous aurez également un `ADBMobileConfig.json` fichier. Pour plus d’informations sur ce fichier, voir le fichier [de configuration](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Différents `.dll/.winmd` fichiers sont fournis pour chaque architecture prise en charge (x86, x64, ARM).

>[!IMPORTANT]
>
>La version de `ADBMobile.winmd` ne reflète pas la version de la bibliothèque. Le `.winmd` fichier contient uniquement des métadonnées et un numéro de version de `255.255.255.255`, ce qui est accepté par Microsoft. Pour plus d&#39;informations, consultez [Comment ajouter des informations d&#39;assemblage pour une dll de composant WinRT C++ / CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Pour vérifier la version de la bibliothèque que vous utilisez, vérifiez la version du `ADBMobile.dll` fichier sous-jacent.

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque de plateformes Windows universelles peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide se trouvent dans WinJS (JavaScript), si vous utilisez un autre langage, il peut être nécessaire de le modifier. Lorsque vous utilisez des méthodes winmd de winJS, toutes les méthodes ont automatiquement leur première lettre minuscule.

La principale différence entre les implémentations est la structure de données utilisée pour les données contextuelles. De plus, lors de l’utilisation du SDK dans un projet WinJS, utilisez une chaîne vide ( `""` ou `''`) au lieu de `null` valeurs de chaîne vides.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l’Explorateur **[!UICONTROL de]** solutions, cliquez avec le bouton droit sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter la référence]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir *Sélection de la section de version* correcte sur cette page.

1. Cliquez sur **Ajouter**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la fenêtre Gestionnaire **[!UICONTROL de]** références et cliquez sur **[!UICONTROL OK]**.

1. Dans l’Explorateur **[!UICONTROL de]** solutions, cliquez avec le bouton droit sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter la référence]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l’onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]**, sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications]** de plateformes Windows universelles.

1. Ajoutez la ligne suivante à votre classe :

   ```csharp
   using ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet et cliquez sur **[!UICONTROL Ajouter]** > Elément **** existant.

1. Accédez au `ADBMobileConfig.json` fichier et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le `ADBMobileConfig.json` fichier de votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Remplacez l’action **** Build par **[!UICONTROL Contenu]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l’Explorateur **[!UICONTROL de]** solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Références]**.

1. Sélectionnez la version correcte de la bibliothèque et ajoutez une référence au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir *Sélection de la section de version* correcte sur cette page.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la fenêtre Gestionnaire **[!UICONTROL de]** références, puis cliquez sur **[!UICONTROL OK]**.

1. Ajoutez la ligne suivante à votre classe :

   ```c++
   using namespace ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > Elément **** existant.

1. Accédez au `ADBMobileConfig.json` fichier et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le `ADBMobileConfig.json` fichier dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Dans l’onglet **[!UICONTROL Général]** , remplacez **[!UICONTROL Contenu]** par **[!UICONTROL Oui]** et cliquez sur **[!UICONTROL OK.]**

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio et ouvrez votre solution.

1. Dans l’Explorateur **[!UICONTROL de]** solutions, cliquez avec le bouton droit sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter la référence]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la fenêtre Gestionnaire **[!UICONTROL de]** références et cliquez sur **[!UICONTROL OK]**.

1. Dans l’Explorateur **[!UICONTROL de]** solutions, cliquez avec le bouton droit sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter la référence]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l’onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]** , puis sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications]** de plateformes Windows universelles.

1. Cliquez avec le bouton droit de la souris sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > Elément **** existant.

1. Accédez au `ADBMobileConfig.json` fichier et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le `ADBMobileConfig.json` fichier dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Lorsque les propriétés **** de fichier sont sélectionnées, vérifiez que l’action **[!UICONTROL de]** package est définie sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur Contenu par défaut.

## Mise à jour du fichier de configuration ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Le `ADBMobileConfig.json` fichier contient les paramètres du SDK global et se trouve à la racine du projet une fois que vous avez terminé les étapes de l’ *Ajoute de la bibliothèque et du fichier de configuration à la section du projet* . Si votre `ADBMobileConfig.json` fichier n’a pas été préconfiguré par Adobe Mobile Services, vous devez mettre à jour quelques valeurs pour commencer.

Voici un exemple de fichier `ADBMobileConfig.json` :

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Mettez à jour au minimum les valeurs suivantes pour les solutions que vous utilisez :

* **Adobe Analytics**: `rsids` et `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Pour activer le débogage pour le SDK, appelez `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JavaScript, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut pour les applications C++) :

### C Sharp

1. Cliquez avec le bouton droit sur le projet, cliquez sur **[!UICONTROL Propriétés]** > onglet **** Débogage.

1. La liste déroulante Type de débogueur devient **natif uniquement**.

### JavaScript

1. Cliquez avec le bouton droit sur le projet, cliquez sur **[!UICONTROL Propriétés]** > Propriétés **[!UICONTROL de]** configuration > onglet **** Débogage.

1. La liste déroulante Type de débogueur devient **[!UICONTROL natif uniquement]**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en oeuvre Analytics, Cible et Audience Management dans votre application de plateforme Windows universelle.


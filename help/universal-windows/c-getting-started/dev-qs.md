---
description: Informations sur la mise en oeuvre de la bibliothèque de plateformes Windows universelles.
solution: Experience Cloud,Analytics
title: Démarrage rapide pour les développeurs
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# Démarrage rapide pour les développeurs{#developer-quick-start}

Voici quelques informations sur la mise en oeuvre de la bibliothèque de plateformes Windows universelles.

>[!IMPORTANT]
>
>Pour mettre en oeuvre le SDK, vous devez disposer de Visual Studio 2013 ou version ultérieure.

## Obtention du kit SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le fichier [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plate-forme prise en charge. Vous aurez également un fichier `ADBMobileConfig.json`. Pour plus d’informations sur ce fichier, voir [Fichier de configuration ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Sélectionnez la version {#section_E53C5AA7D5474824A89BB32C003865A1} appropriée.

Différents fichiers `.dll/.winmd` sont fournis pour chaque architecture prise en charge (x86, x64, ARM).

>[!IMPORTANT]
>
>La version de `ADBMobile.winmd` ne reflète pas la version de la bibliothèque. Le fichier `.winmd` contient uniquement des métadonnées et a le numéro de version `255.255.255.255`, qui est accepté par Microsoft. Pour plus d&#39;informations, voir [Comment ajouter des informations d&#39;assemblage pour une dll de composant WinRT C++ / CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Pour vérifier la version de la bibliothèque que vous utilisez, vérifiez la version du fichier `ADBMobile.dll` sous-jacent.

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque de plateformes Windows universelles peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide se trouvent dans WinJS (JavaScript), si vous utilisez un autre langage, il peut être nécessaire de le modifier. Lorsque vous utilisez des méthodes winmd de winJS, toutes les méthodes ont automatiquement leur première lettre minuscule.

La principale différence entre les implémentations est la structure de données utilisée pour les données contextuelles. De plus, lorsque vous utilisez le SDK dans un projet WinJS, utilisez une chaîne vide ( `""` ou `''`) au lieu de `null` pour les valeurs de chaîne vides.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir la section *Sélectionner la version correcte* de cette page.

1. Cliquez sur **Ajouter**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la fenêtre **[!UICONTROL Gestionnaire de références]** et cliquez sur **[!UICONTROL OK]**.

1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l&#39;onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]**, sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Ajoutez la ligne suivante à votre classe :

   ```csharp
   using ADBMobile;
   ```

1. Cliquez avec le bouton droit sur votre projet et cliquez sur **[!UICONTROL Ajouter]** > **[!UICONTROL Elément existant]**.

1. Accédez au fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Remplacez **[!UICONTROL Build Action]** par **[!UICONTROL Content]**.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Références]**.

1. Sélectionnez la version correcte de la bibliothèque et ajoutez une référence au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir la section *Sélectionner la version correcte* de cette page.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la fenêtre **[!UICONTROL Gestionnaire de références]** et cliquez sur **[!UICONTROL OK]**.

1. Ajoutez la ligne suivante à votre classe :

   ```c++
   using namespace ADBMobile;
   ```

1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Elément existant]**.

1. Accédez au fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Sous l&#39;onglet **[!UICONTROL Général]**, remplacez **[!UICONTROL Contenu]** par **[!UICONTROL Oui]** et cliquez sur **[!UICONTROL OK]**.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio et ouvrez votre solution.

1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la fenêtre **[!UICONTROL Gestionnaire de références]** et cliquez sur **[!UICONTROL OK]**.

1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l&#39;onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]** et sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications de plateformes Windows universelles]**.

1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Elément existant]**.

1. Accédez au fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Si **[!UICONTROL Propriétés du fichier]** est sélectionné, vérifiez que **[!UICONTROL Action du package]** est définie sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur Contenu par défaut.

## Mise à jour du fichier de configuration ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Le fichier `ADBMobileConfig.json` contient des paramètres SDK globaux et se trouve à la racine de votre projet après avoir suivi les étapes de la section *Ajouter le fichier de bibliothèque et de configuration à votre projet*. Si votre fichier `ADBMobileConfig.json` n&#39;a pas été préconfiguré par Adobe Mobile Services, vous devez mettre à jour quelques valeurs pour commencer.

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

* **Adobe Analytics** :  `rsids` et  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Pour plus d’informations, voir [Méthodes SDK](/help/universal-windows/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Pour activer le débogage pour le SDK, appelez `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JavaScript, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut pour les applications C++) :

### C Sharp

1. Cliquez avec le bouton droit sur le projet, cliquez sur **[!UICONTROL Propriétés]** > **[!UICONTROL onglet Débogage]**.

1. Remplacez la liste déroulante du type de débogueur par **Native Only**.

### JavaScript

1. Cliquez avec le bouton droit sur le projet, cliquez sur **[!UICONTROL Propriétés]** > **[!UICONTROL Propriétés de configuration]** > **[!UICONTROL Onglet Débogage]**.

1. Remplacez la liste déroulante du type de débogueur par **[!UICONTROL Native Only]**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en oeuvre Analytics, Cible et Audience Management dans votre application de plateforme Windows universelle.

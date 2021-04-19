---
description: 'null'
seo-description: 'null'
seo-title: Démarrage rapide pour les développeurs
solution: Experience Cloud,Analytics
title: Démarrage rapide pour les développeurs
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---

# Démarrage rapide pour les développeurs {#developer-quick-start}

Vous aurez besoin de Visual Studio 2013 ou version ultérieure pour mettre en oeuvre le SDK.

## Obtention du kit SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le [téléchargement du SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plate-forme prise en charge. Vous disposerez également d&#39;un fichier `ADBMobileConfig.json` qui est expliqué plus loin dans ce guide.

## Sélectionnez la version {#section_E53C5AA7D5474824A89BB32C003865A1} appropriée.

Différents fichiers `.dll`/ `.winmd` sont fournis pour chaque plate-forme de cible (Windows 8.1, Windows Phone 8.1) et l’architecture prise en charge (x86, x64, ARM). Les fichiers sont séparés dans une structure de dossiers selon les éléments suivants :

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La version de `ADBMobile.winmd` ne reflète pas la version de la bibliothèque. Le fichier `.winmd` contient uniquement des métadonnées et, en tant que tel, aura un numéro de version de `255.255.255.255` qui est le comportement accepté par Microsoft (voir [Comment puis-je ajouter des informations d&#39;assemblage pour une dll de composant WinRT C++ / CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Pour vérifier la version de la bibliothèque que vous utilisez, vérifiez la version du fichier `ADBMobile.dll` sous-jacent.

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque Windows 8.1 Universal App Store peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide se trouvent dans WinJS (JavaScript) et doivent peut-être être modifiés si vous utilisez un autre langage. Notez que lorsque vous utilisez des méthodes winmd de winJS (JavaScript), toutes les méthodes ont automatiquement leur première lettre avec un caractère minuscule.

La principale différence entre les implémentations est la structure de données utilisée pour les données contextuelles.

De plus, lorsque vous utilisez le SDK dans un projet WinJS, utilisez une chaîne vide ( `""` ou `''`) au lieu de `null` pour les valeurs de chaîne vides.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l&#39;**Explorateur de solutions**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

1. Sélectionnez la version correcte de la bibliothèque et recherchez le fichier `ADBMobile.winmd` associé.

   Pour plus d’informations, voir la section *Sélectionner la version correcte* ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est sélectionné dans la fenêtre **[!UICONTROL Gestionnaire de références]** et cliquez sur **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Lors de l&#39;ajout d&#39;une référence à une application Windows Phone, pour sélectionner `ADBMobile.winmd`, remplacez le filtre de fichier par défaut **[!UICONTROL Fichiers composants]** par **Tous les fichiers**.

1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

   Ignorez cette étape si votre solution contient également un projet C++.

1. Dans l&#39;onglet **Windows** sur la gauche, sélectionnez **[!UICONTROL Extensions]**, puis sélectionnez et ajoutez **[!UICONTROL Package d&#39;exécution Microsoft Visual C++ 2013 pour Windows]**.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez à votre fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Remplacez **[!UICONTROL Build Action]** par **[!UICONTROL Content]**.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Références]**.

1. Sélectionnez la version correcte de la bibliothèque, puis ajoutez une référence au fichier `ADBMobile.winmd` associé.

   Pour plus d’informations, voir la section *Sélectionner la version appropriée* ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Dans la fenêtre **[!UICONTROL Gestionnaire de références]**, vérifiez que `ADBMobile.winmd` est sélectionné et cliquez sur **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Lors de l&#39;ajout d&#39;une référence à une application Windows Phone, pour sélectionner `ADBMobile.winmd`, remplacez le filtre de fichier par défaut **[!UICONTROL Fichiers composants]** par **Tous les fichiers**.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using namespace ADMS::Measurement;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez au fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Sous l&#39;onglet **[!UICONTROL Général]**, remplacez **[!UICONTROL Contenu]** par **[!UICONTROL Oui]**, puis cliquez sur **[!UICONTROL OK]**.

## Ajouter la bibliothèque et le fichier de configuration à votre projet - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans l&#39;**Explorateur de solutions**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

   Pour plus d’informations, voir la section *Sélectionner la version appropriée* ci-dessous.

1. Sélectionnez la version correcte de la bibliothèque, puis recherchez le fichier `ADBMobile.winmd` associé.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la fenêtre **[!UICONTROL Gestionnaire de références]** et cliquez sur **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Lors de l&#39;ajout d&#39;une référence à une application Windows Phone, pour sélectionner `ADBMobile.winmd`, remplacez le filtre de fichier par défaut **[!UICONTROL Fichiers composants]** par **Tous les fichiers**.

1. Dans l&#39;**[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Référence de l&#39;Ajoute]**.

   Ignorez cette étape si votre solution contient également un projet C++.

1. Dans l&#39;onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]** et sélectionnez et ajoutez **[!UICONTROL Package d&#39;exécution Microsoft Visual C++ 2013 pour Windows]**.

1. Cliquez avec le bouton droit sur votre projet et sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Elément existant]**.

1. Accédez au fichier `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit sur le fichier `ADBMobileConfig.json]` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Si **[!UICONTROL Propriétés du fichier]** est sélectionné, vérifiez que **[!UICONTROL Action du package]** est définie sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur **[!UICONTROL Contenu]** par défaut.

## Mise à jour du fichier de configuration ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Le fichier `ADBMobileConfig.json` contient des paramètres SDK globaux et se trouve à la racine de votre projet après avoir suivi les étapes de la section *Ajouter la bibliothèque et le fichier de configuration à votre projet*. Si votre fichier `ADBMobileConfig.json` n&#39;a pas été préconfiguré par Adobe Mobile Services, vous devez mettre à jour quelques valeurs pour commencer.

Voici un exemple de fichier `ADBMobileConfig.json` :

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

Au minimum, mettez à jour les valeurs suivantes pour les solutions que vous utilisez :

* **Analytics** :  `rsids` et  `server`
* **Target**: `clientCode`
* **Gestion des** Audiences :  `server`

Pour plus d’informations, voir [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Pour activer le débogage pour le SDK, vous devez appeler `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JS, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut pour les applications C++) :

### C Sharp

Cliquez avec le bouton droit sur le projet, sélectionnez **[!UICONTROL Propriétés]** > **[!UICONTROL onglet Débogage]**. Dans la liste déroulante du débogueur, sélectionnez **[!UICONTROL natif uniquement]**.

### JS

Cliquez avec le bouton droit sur le projet, sélectionnez **[!UICONTROL Propriétés]** > **[!UICONTROL Propriétés de configuration]** > **[!UICONTROL Onglet Débogage]**. Remplacez la liste déroulante du type de débogueur par **Native Only**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en oeuvre Analytics, Cible et Audience Management dans votre application Windows 8.1 Universal App Store.

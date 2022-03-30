---
description: Article de démarrage rapide pour les développeurs
solution: Experience Cloud Services,Analytics
title: Démarrage rapide pour les développeurs
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Démarrage rapide pour les développeurs {#developer-quick-start}

Vous aurez besoin de Visual Studio 2013 ou version ultérieure pour mettre en oeuvre le SDK.

## Obtention du kit SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le fichier [Téléchargement du SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plateforme prise en charge. Vous trouverez également un `ADBMobileConfig.json` qui est expliqué plus loin dans ce guide.

## Sélectionner la version correcte {#section_E53C5AA7D5474824A89BB32C003865A1}

Différent `.dll`/ `.winmd` Les fichiers sont fournis pour chaque plateforme cible (Windows 8.1, Windows Phone 8.1) et l’architecture prise en charge (x86, x64, ARM). Les fichiers sont séparés dans une structure de dossiers selon ce qui suit :

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La version de `ADBMobile.winmd` ne reflète pas la version de la bibliothèque. Le `.winmd` contient des métadonnées uniquement et, en tant que tel, dispose d’un numéro de version de `255.255.255.255` qui est le comportement accepté en fonction de Microsoft (voir [Comment ajouter des informations d’assemblage pour une DLL de composant WinRT C++/CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Pour vérifier la version de la bibliothèque que vous utilisez, vérifiez la version de la `ADBMobile.dll` fichier .

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque App Store universelle Windows 8.1 peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide sont dans WinJS (JavaScript) et doivent peut-être être être modifiés si vous utilisez un autre langage. Notez que lorsque vous utilisez des méthodes winmd à partir de winJS (JavaScript), toutes les méthodes reçoivent automatiquement leur première lettre en minuscules.

La principale différence entre les mises en oeuvre est la structure de données utilisée pour les données contextuelles.

En outre, lors de l’utilisation du SDK dans un projet WinJS, utilisez une chaîne vide ( `""` ou `''`) au lieu de `null` pour les valeurs de chaîne vides.

## Ajoutez la bibliothèque et le fichier de configuration à votre projet - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans le **Explorateur de solutions**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez à la `ADBMobile.winmd` fichier .

   Pour plus d’informations, voir *Sélectionner la version correcte* ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est sélectionné dans la variable **[!UICONTROL Gestionnaire de références]** puis cliquez sur **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Lors de l’ajout d’une référence à une application Windows Phone, sélectionnez `ADBMobile.winmd`, modifiez le filtre de fichier par défaut à partir de **[!UICONTROL Fichiers de composant]** to **Tous les fichiers**.

1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

   Ignorez cette étape si votre solution contient également un projet C++.

1. Dans le **Windows** à gauche, sélectionnez **[!UICONTROL Extensions]**, puis sélectionnez et ajoutez **[!UICONTROL Package d’exécution Microsoft Visual C++ 2013 pour Windows]**.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez à `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Modifier **[!UICONTROL Création d’une action]** to **[!UICONTROL Contenu]**.

## Ajoutez la bibliothèque et le fichier de configuration à votre projet - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans le **[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Références]**.

1. Sélectionnez la version correcte de la bibliothèque, puis ajoutez une référence à la `ADBMobile.winmd` fichier .

   Pour plus d’informations, voir *Sélection de la version appropriée* ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Dans le **[!UICONTROL Gestionnaire de références]** , vérifiez que `ADBMobile.winmd` est sélectionné et cliquez sur **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Lors de l’ajout d’une référence à une application Windows Phone, sélectionnez `ADBMobile.winmd`, modifiez le filtre de fichier par défaut à partir de **[!UICONTROL Fichiers de composant]** to **Tous les fichiers**.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using namespace ADMS::Measurement;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez au `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Sur le **[!UICONTROL Général]** onglet, modifier **[!UICONTROL Contenu]** to **[!UICONTROL Oui]**, puis cliquez sur **[!UICONTROL OK]**.

## Ajout de la bibliothèque et du fichier de configuration à votre projet - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans le **Explorateur de solutions**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

   Pour plus d’informations, voir *Sélection de la version appropriée* ci-dessous.

1. Sélectionnez la version correcte de la bibliothèque, puis accédez à la `ADBMobile.winmd` fichier .

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la variable **[!UICONTROL Gestionnaire de références]** puis cliquez sur **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Lors de l’ajout d’une référence à une application Windows Phone, sélectionnez `ADBMobile.winmd`, modifiez le filtre de fichier par défaut à partir de **[!UICONTROL Fichiers de composant]** to **Tous les fichiers**.

1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

   Ignorez cette étape si votre solution contient également un projet C++.

1. Dans le **[!UICONTROL Windows]** à gauche, sélectionnez **[!UICONTROL Extensions]** et sélectionnez et ajoutez **[!UICONTROL Package d’exécution Microsoft Visual C++ 2013 pour Windows]**.

1. Cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez au `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json]` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Avec **[!UICONTROL Propriétés du fichier]** sélectionné, assurez-vous que **[!UICONTROL Action de package]** est défini sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur **[!UICONTROL Contenu]** par défaut.

## Mise à jour du fichier de configuration ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Le `ADBMobileConfig.json` contient les paramètres du SDK global et se trouve à la racine de votre projet une fois que vous avez terminé les étapes de la section *Ajout de la bibliothèque et du fichier de configuration au projet* . Si votre `ADBMobileConfig.json` n’a pas été préconfiguré par Adobe Mobile Services. Vous devez mettre à jour quelques valeurs pour commencer.

Voici un exemple d’une `ADBMobileConfig.json` fichier :

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

* **Analytics**: `rsids` et `server`
* **Target**: `clientCode`
* **Gestion de l’audience**: `server`

Pour plus d’informations, voir [Fichier de configuration ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Pour activer le débogage pour le SDK, vous devez appeler `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JS, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut des applications C++) :

### Accentuation C

Cliquez avec le bouton droit sur le projet, puis sélectionnez **[!UICONTROL Propriétés]** > **[!UICONTROL Onglet Débogage]**. Dans la liste déroulante du débogueur, sélectionnez **[!UICONTROL natif uniquement]**.

### JS

Cliquez avec le bouton droit sur le projet, puis sélectionnez  **[!UICONTROL Propriétés]** > **[!UICONTROL Propriétés de configuration]** > **[!UICONTROL Onglet Débogage]**. Définissez la liste déroulante de type de débogueur sur **natif uniquement**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en oeuvre Analytics, Target et la gestion de l’audience dans votre application Windows 8.1 Universal App Store.

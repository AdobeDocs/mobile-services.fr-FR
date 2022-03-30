---
description: Informations sur la mise en oeuvre de la bibliothèque Plateforme Windows universelle.
solution: Experience Cloud Services,Analytics
title: Démarrage rapide pour les développeurs
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# Démarrage rapide pour les développeurs{#developer-quick-start}

Voici quelques informations sur la mise en oeuvre de la bibliothèque Plateforme Windows universelle.

>[!IMPORTANT]
>
>Pour mettre en oeuvre le SDK, vous devez disposer de Visual Studio 2013 ou d’une version ultérieure.

## Obtention du kit SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le fichier [Téléchargement du SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) , vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plate-forme prise en charge. Vous trouverez également un `ADBMobileConfig.json` fichier . Pour plus d’informations sur ce fichier, voir [Fichier de configuration ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Sélectionner la version correcte {#section_E53C5AA7D5474824A89BB32C003865A1}

Différent `.dll/.winmd` Les fichiers sont fournis pour chaque architecture prise en charge (x86, x64, ARM).

>[!IMPORTANT]
>
>La version de `ADBMobile.winmd` ne reflète pas la version de la bibliothèque. Le `.winmd` contient uniquement des métadonnées et un numéro de version de `255.255.255.255`, qui est le comportement accepté selon Microsoft. Pour plus d’informations, voir [Comment ajouter des informations d’assemblage pour une DLL de composant WinRT C++/CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Pour vérifier la version de la bibliothèque que vous utilisez, vérifiez la version de la `ADBMobile.dll` fichier .

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque Plateforme Windows universelle peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide sont dans WinJS (JavaScript). Si vous utilisez un autre langage, il peut être nécessaire de le modifier. Lorsque vous utilisez des méthodes winmd à partir de winJS, toutes les méthodes reçoivent automatiquement leur première lettre en minuscules.

La principale différence entre les mises en oeuvre est la structure de données utilisée pour les données contextuelles. En outre, lors de l’utilisation du SDK dans un projet WinJS, utilisez une chaîne vide ( `""` ou `''`) au lieu de `null` pour les valeurs de chaîne vides.

## Ajout de la bibliothèque et du fichier de configuration au projet - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir *Sélectionner la version correcte* sur cette page.

1. Cliquez sur **Ajouter**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la variable **[!UICONTROL Gestionnaire de références]** puis cliquez sur **[!UICONTROL OK]**.

1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans le **[!UICONTROL Windows]** à gauche, sélectionnez **[!UICONTROL Extensions]**, sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications de plateforme Windows universelle]**.

1. Ajoutez la ligne suivante à votre classe :

   ```csharp
   using ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet, puis cliquez sur **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez au `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Modifier **[!UICONTROL Création d’une action]** to **[!UICONTROL Contenu]**.

## Ajoutez la bibliothèque et le fichier de configuration à votre projet - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio et ouvrez votre solution.
1. Dans le **[!UICONTROL Explorateur de solutions]**, cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Références]**.

1. Sélectionnez la version correcte de la bibliothèque et ajoutez une référence au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir *Sélectionner la version correcte* sur cette page.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la variable **[!UICONTROL Gestionnaire de références]** puis cliquez sur **[!UICONTROL OK]**.

1. Ajoutez la ligne suivante à votre classe :

   ```c++
   using namespace ADBMobile;
   ```

1. Cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez à `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Sur le **[!UICONTROL Général]** onglet, modifier **[!UICONTROL Contenu]** to **[!UICONTROL Oui]** et cliquez sur **[!UICONTROL OK]**.

## Ajout de la bibliothèque et du fichier de configuration à votre projet - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio et ouvrez votre solution.

1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que le fichier ADBMobile.winmd est coché dans la variable **[!UICONTROL Gestionnaire de références]** puis cliquez sur **[!UICONTROL OK]**.

1. Dans le **[!UICONTROL Explorateur de solutions]**, clic droit **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Ajouter une référence]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans le **[!UICONTROL Windows]** à gauche, sélectionnez **[!UICONTROL Extensions]** et sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications de plateforme Windows universelle]**.

1. Cliquez avec le bouton droit de la souris sur votre projet, puis sélectionnez **[!UICONTROL Ajouter]** > **[!UICONTROL Élément existant]**.

1. Accédez au `ADBMobileConfig.json` et cliquez sur **[!UICONTROL Ajouter]**.

1. Cliquez avec le bouton droit de la souris sur le `ADBMobileConfig.json` dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Avec **[!UICONTROL Propriétés du fichier]** sélectionné, assurez-vous que **[!UICONTROL Action de package]** est défini sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur Contenu par défaut.

## Mise à jour du fichier de configuration ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Le `ADBMobileConfig.json` contient les paramètres du SDK global et se trouve à la racine de votre projet une fois que vous avez terminé les étapes de la section *Ajout de la bibliothèque et du fichier de configuration au projet* . Si votre `ADBMobileConfig.json` n’a pas été préconfiguré par Adobe Mobile Services. Vous devez mettre à jour quelques valeurs pour commencer.

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

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Pour plus d’informations, voir [Méthodes SDK](/help/universal-windows/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Pour activer le débogage pour le SDK, appelez `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JavaScript, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut des applications C++) :

### Accentuation C

1. Cliquez avec le bouton droit sur le projet, puis cliquez sur  **[!UICONTROL Propriétés]** > **[!UICONTROL Onglet Débogage]**.

1. Définissez la liste déroulante de type de débogueur sur **natif uniquement**.

### JavaScript

1. Cliquez avec le bouton droit sur le projet, puis cliquez sur **[!UICONTROL Propriétés]** > **[!UICONTROL Propriétés de configuration]** > **[!UICONTROL Onglet Débogage]**.

1. Définissez la liste déroulante de type de débogueur sur **[!UICONTROL natif uniquement]**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en oeuvre Analytics, Target et la gestion de l’audience dans votre application Plateforme Windows universelle.

---
description: valeur nulle
seo-description: valeur nulle
seo-title: 'Développeurs : démarrage rapide'
solution: Marketing Cloud,Analytics
title: 'Développeurs : démarrage rapide'
topic: Développeur et mise en œuvre
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Voici quelques informations sur la mise en oeuvre de la bibliothèque de plateformes Windows universelles.

>[!IMPORTANT]
>
>Pour mettre en oeuvre le SDK, vous devez disposer de Visual Studio 2013 ou version ultérieure.

## Obtention du kit SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. Vous aurez également un `ADBMobileConfig.json` fichier. Pour plus d’informations sur ce fichier, voir Fichier [de configuration](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. Le `.winmd` fichier contient uniquement des métadonnées et possède un numéro de version de `255.255.255.255`, qui est accepté par Microsoft. Pour plus d'informations, consultez [Comment ajouter des informations d'assemblage pour une dll de composant WinRT C++ / CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Différences de syntaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque Plateforme Windows universelle peut être utilisée dans plusieurs langages de programmation. Les exemples de ce guide sont dans WinJS (JavaScript). Si vous utilisez un autre langage, il se peut que vous deviez le modifier. Lorsque vous utilisez des méthodes winmd de winJS, toutes les méthodes ont automatiquement leur première lettre lue.

La principale différence entre les mises en œuvre réside dans la structure des données utilisée pour les données contextuelles. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio, puis ouvrez la solution.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version  of the library and browse to the associated ADBMobile.winmd file.

   Pour plus d’informations, voir *Sélection de la section Version* correcte sur cette page.

1. Cliquez sur **Ajouter**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l’onglet **[!UICONTROL Windows]** de gauche, sélectionnez **[!UICONTROL Extensions]**, sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications de plateformes]** Windows universelles.

1. Ajoutez la ligne suivante à votre classe :

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Cliquez avec le bouton droit sur le `ADBMobileConfig.json` fichier dans votre solution et sélectionnez **[!UICONTROL Propriétés]**.

1. Définissez **[!UICONTROL Action de génération]** sur **[!UICONTROL Contenu]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio, puis ouvrez la solution.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Sélectionnez la version correcte de la bibliothèque et ajoutez une référence au fichier ADBMobile.winmd associé.

   Pour plus d’informations, voir *Sélection de la section Version* correcte sur cette page.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la fenêtre **Gestionnaire de références**, puis cliquez sur **[!UICONTROL OK]**.

1. Ajoutez la ligne suivante à votre classe :

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio, puis ouvrez la solution.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Sélectionnez la version correcte de la bibliothèque et accédez au fichier ADBMobile.winmd associé.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si votre solution contient également un projet C++, ignorez cette étape.

1. Dans l’onglet **[!UICONTROL Windows]** sur la gauche, sélectionnez **[!UICONTROL Extensions]** , puis sélectionnez et ajoutez **[!UICONTROL Visual C++ 2015 Runtime pour les applications de plateformes]** Windows universelles.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Les propriétés **[!UICONTROL du]** fichier étant sélectionnées, assurez-vous que l’action **[!UICONTROL du]** package est définie sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini sur Contenu par défaut.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

* **Adobe Analytics:  and**`rsids``server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Pour plus d’informations, voir Méthodes [de](/help/universal-windows/c-configuration/methods.md)SDK.

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

To enable debugging for the SDK, call `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JavaScript, vous devez activer le débogage du code natif en procédant comme suit (le débogage du code natif est le paramètre par défaut pour les applications C++) :

### C Sharp

1. Right-click the project, click  **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Définissez le menu déroulant du type de débogueur sur **Natif uniquement**.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Définissez le menu déroulant du type de débogueur sur **[!UICONTROL Natif uniquement]**.

Vous avez terminé ! Vous êtes maintenant prêt à mettre en œuvre Analytics, Target et la gestion de l’audience dans votre application Plateforme Windows universelle.


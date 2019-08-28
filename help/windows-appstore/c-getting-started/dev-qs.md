---
description: valeur nulle
seo-description: valeur nulle
seo-title: Démarrage rapide des développeurs
solution: Marketing Cloud, Analytics
title: Démarrage rapide des développeurs
topic: Développeur et mise en œuvre
uuid: b 368959 b-d 985-436 e -8 b 3 e -97 e 355 a 97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

Vous aurez besoin de la version 2013 ou ultérieure de Visual Studio pour mettre en œuvre le SDK.

## Obtention du SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Après avoir décompressé le fichier de [téléchargement du SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), vous disposez d’un dossier distinct pour chaque combinaison d’architecture et de plate-forme prise en charge. Vous disposez également d’un fichier `ADBMobileConfig.json` expliqué plus loin dans ce guide.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). Les fichiers sont séparés en une structure de dossiers comme suit :

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` Le fichier contient uniquement des métadonnées et, pour ce faire, un numéro de version `255.255.255.255` dont le comportement est accepté conformément à Microsoft (voir [Comment ajouter des informations d'assemblage pour un composant winrt C + +/CX ?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

La bibliothèque Boutique d’applications Windows 8.1 universelle peut être utilisée dans plusieurs langages de programmation. Les exemples fournis dans ce guide sont en WinJS (JavaScript) et devront peut-être être modifiés si vous utilisez un autre langage. Notez que lorsque vous utilisez des méthodes winmd à partir de winJS (JavaScript), la première lettre de toutes les méthodes est automatiquement en minuscule.

La principale différence entre les mises en œuvre réside dans la structure des données utilisée pour les données contextuelles.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Lancez Visual Studio, puis ouvrez la solution.
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **[!UICONTROL Références]**, puis sélectionnez **[!UIUCONTROL Ajouter une référence]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   Pour plus d'informations, consultez *la section Sélectionner la version* correcte ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Lors de l'ajout d'une référence à une application Windows Phone, sélectionnez le `ADBMobile.winmd`filtre de fichier par défaut à partir de Fichiers **[!UICONTROL composants]** dans **Tous les fichiers**&#x200B;à sélectionner.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Ignorez cette étape si vous avez également un projet. c. + + dans votre solution.

1. Dans l'onglet **Windows** situé à gauche, sélectionnez **[!UICONTROL Extensions]**, puis sélectionnez et ajoutez **[!UICONTROL le package d'exécution Microsoft Visual C + + 2013 pour Windows]**.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Accédez à `ADBMobileConfig.json` votre fichier et cliquez **[!UICONTROL sur Ajouter]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Définissez **[!UICONTROL Action de génération]** sur **[!UICONTROL Contenu]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Lancez Visual Studio, puis ouvrez la solution.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   Pour plus d'informations, reportez-vous à *la section Sélectionner la version* correcte ci-dessous.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Dans **[!UICONTROL la fenêtre Gestionnaire]** de références, vérifiez que `ADBMobile.winmd` l'option est sélectionnée et cliquez **[!UICONTROL sur OK]**.

   >[!TIP]
   >
   >Lors de l'ajout d'une référence à une application Windows Phone, sélectionnez le `ADBMobile.winmd`filtre de fichier par défaut à partir de Fichiers **[!UICONTROL composants]** dans **Tous les fichiers**&#x200B;à sélectionner.

1. Ajoutez la ligne suivante à votre classe :

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Lancez Visual Studio, puis ouvrez la solution.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   Pour plus d'informations, consultez *la section Sélection de la version* correcte ci-dessous.

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Vérifiez que `ADBMobile.winmd` est coché dans la fenêtre **Gestionnaire de références**, puis cliquez sur **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Lors de l'ajout d'une référence à une application Windows Phone, sélectionnez le `ADBMobile.winmd`filtre de fichier par défaut à partir de Fichiers **[!UICONTROL composants]** dans **Tous les fichiers**&#x200B;à sélectionner.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Ignorez cette étape si vous avez également un projet. c. + + dans votre solution.

1. Dans l'onglet **[!UICONTROL Windows]** situé à gauche, sélectionnez **[!UICONTROL Extensions]** , puis sélectionnez et ajoutez **[!UICONTROL le package d'exécution Microsoft Visual C + + 2013 pour Windows]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. Lorsque les propriétés **[!UICONTROL du fichier]** sont sélectionnées, assurez-vous **[!UICONTROL que l'action]** de package est définie sur **[!UICONTROL Contenu]**.

   Pour les projets JavaScript, le fichier est défini par défaut sur **[!UICONTROL Contenu]** .

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` Le fichier contient des paramètres SDK globaux, qui se trouvent à la racine de votre projet après avoir renseigné la section *Ajouter la bibliothèque et le fichier de configuration à votre projet* . If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

Mettez au moins à jour les valeurs suivantes pour les solutions que vous utilisez :

* **Analytics**: `rsids` et `server`
* **Target**: `clientCode`
* **Gestion de l’audience**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Débogage {#section_3A10376A60394A15BEE483323E0CD4AA}

Lorsque vous souhaitez activer le débogage pour le SDK, vous devez appeler `ADBMobile.Config.setDebugLogging(true);`.

Pour les applications C Sharp et JS, vous devez activer le débogage du code natif en exécutant les étapes suivantes (le débogage du code natif est le paramètre par défaut pour les applications C + +) :

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. Dans la liste déroulante Débogueur, sélectionnez **[!UICONTROL Natif uniquement]**.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. Définissez le menu déroulant du type de débogueur sur **Natif uniquement**.

Vous avez terminé. Vous êtes maintenant prêt à mettre en œuvre Analytics, Target et la gestion de l’audience dans l’application Boutique d’applications Windows 8.1 universelle.

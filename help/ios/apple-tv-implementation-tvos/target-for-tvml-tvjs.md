---
description: Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs dans vos fichiers .xml. Indiquez les zones de votre page à remplacer par du contenu Target en utilisant l’élément XML ADBTarget personnalisé.
seo-description: Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs dans vos fichiers .xml. Indiquez les zones de votre page à remplacer par du contenu Target en utilisant l’élément XML ADBTarget personnalisé.
seo-title: Adobe Target pour TVML/TVJS
title: Adobe Target pour TVML/TVJS
uuid: afd 5 a 583-5266-43 f 2-8 cb 0-0 ace 89 c 53 a 57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target pour TVML/TVJS{#adobe-target-for-tvml-tvjs}

Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs dans vos fichiers .xml. Indiquez les zones de votre page à remplacer par du contenu Target en utilisant l’élément XML ADBTarget personnalisé.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. Pour plus d'informations, voir [Mise en œuvre Apple TV avec tvos](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Prise en main {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>Planifiez ce que vous souhaitez remplacer en conséquence.

Votre cas peut se résumer à un simple remplacement de la valeur de chaîne dans une balise ou impliquer une opération plus complexe, comme le remplacement d’une page entière.

## Configuration de l'élément adbtarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Indiquez le nom de dans la propriété `ADBTarget`mbox de l’élément `mbox`. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Nom de l’emplacement de la mbox.

   * Type de propriété : Chaîne
   * Cette propriété est obligatoire.

* **`id`**

   ID de commande.

   * Type de propriété : Chaîne
   * Cette propriété **n** 'est pas obligatoire.

* **`total`**

   Total de la commande.

   * Type de propriété : Chaîne
   * Cette propriété **n** 'est pas obligatoire.

* **`purchasedProductIds`**

   Liste séparée par des virgules des identifiants de produit pour cette commande.

   * Voici l'exemple de code de cette propriété :


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Type de propriété : Chaîne
   * Cette propriété **n** 'est pas obligatoire.

* **`mboxParameters`**

   Liste de paires clé-valeur pour `mboxParameters`. Chaque entrée de cette chaîne est séparée par un point-virgule et les valeurs clés sont séparées par deux points.

   * Voici l'exemple de code de cette propriété :

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Type de propriété : Chaîne
   * Cette propriété **n** 'est pas obligatoire.

* **`customParameterName`**

   La valeur de cette propriété est `customParameterValue`.

   * Type de propriété : Chaîne
   * Cette propriété **n** 'est pas obligatoire.


## Exemples {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Exemple 1

L’exemple suivant utilise un élément `ADBTarget` dans la page `LandingPage.xml.js` pour remplacer le contenu d’une alerte :

#### Configuration de Target

Supposons que le nom de l’emplacement de la mbox soit `landingPage` et que le contenu de l’offre soit défini comme suit :

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### Configuration de landingPage.xml.js

* La configuration de landingPage.xml.js est la suivante :

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* En cas de réussite de la demande vers Target et de renvoi de votre contenu d’offre, votre page se présentera comme suit :

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* S’il n’est pas possible d’atteindre le serveur Target ou si la demande expire, votre page se présentera comme suit :

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Exemple 2

L’exemple suivant indique comment ajouter des données personnalisées à votre élément `ADBTarget`. Cette méthode vous permet de créer des expériences conditionnelles et offre du contenu pour cet emplacement de mbox dans Target :

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```

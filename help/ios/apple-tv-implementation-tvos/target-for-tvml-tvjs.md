---
description: Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs de vos fichiers .xml. Désignez les zones de votre page à remplacer par le contenu de la Cible à l’aide de l’élément XML ADBTarget personnalisé.
seo-description: Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs de vos fichiers .xml. Désignez les zones de votre page à remplacer par le contenu de la Cible à l’aide de l’élément XML ADBTarget personnalisé.
seo-title: Adobe Target pour TVML/TVJS
title: Adobe Target pour TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 70%

---


# Adobe Target pour TVML/TVJS{#adobe-target-for-tvml-tvjs}

Vous pouvez exploiter Adobe Target dans vos applications TVML/TVJS en effectuant des remplacements directs de vos fichiers .xml. Désignez les zones de votre page à remplacer par le contenu de la Cible à l’aide de l’élément XML ADBTarget personnalisé.

>[!IMPORTANT]
>
>Avant d’utiliser l’élément `ADBTarget` dans vos pages TVML, vous devez configurer votre application TVML/TVJS de façon à utiliser le SDK tvOS. Pour plus d’informations, voir [Mise en œuvre de l’Apple TV avec tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Prise en main {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identifiez le fichier `.xml` sur lequel vous souhaitez utiliser l’emplacement cible.
1. Ajoutez un élément `ADBTarget` au fichier en tant qu’enfant de l’élément `<document>`.
1. Si Target ne trouve pas votre emplacement mbox ou s’il expire, la valeur entre les balises `<ADBTarget>` et `</ADBTarget>` est utilisée en tant que contenu par défaut.

## Configuration de votre mbox dans Target {#section_F2DA140C34B0421D976046F825B23123}

Le contenu renvoyé depuis Target remplace l’ensemble du contenu entre `<ADBTarget>` et `</ADBTarget>`, y compris les deux balises `ADBTarget`.

>[!TIP]
>
>Prévoyez ce que vous souhaitez remplacer en conséquence.

Votre cas peut se résumer à un simple remplacement de la valeur de chaîne dans une balise ou impliquer une opération plus complexe, comme le remplacement d’une page entière.

## Configuration de l’élément ADBTarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Indiquez le nom de dans la propriété `ADBTarget`mbox de l’élément `mbox`. Vous pouvez éventuellement ajouter des propriétés personnalisées à votre demande au format `customParameterName="customParameterValue"`.

* **`mbox`**

   Nom de l’emplacement de la mbox.

   * Type de propriété : Chaîne
   * Cette propriété est obligatoire.

* **`id`**

   L’ID de commande.

   * Type de propriété : Chaîne
   * Cette propriété n’est **pas** requise.

* **`total`**

   Total de la commande.

   * Type de propriété : Chaîne
   * Cette propriété n’est **pas** requise.

* **`purchasedProductIds`**

   Liste séparée par des virgules des identifiants de produit pour cette commande.

   * Voici l’exemple de code pour cette propriété :


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Type de propriété : Chaîne
   * Cette propriété n’est **pas** requise.

* **`mboxParameters`**

   Liste de paires clé-valeur pour `mboxParameters`. Chaque entrée de cette chaîne est séparée par un point-virgule (;). Les paires clé-valeur sont séparées par deux-points (:).

   * Voici l’exemple de code pour cette propriété :

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Type de propriété : Chaîne
   * Cette propriété n’est **pas** requise.

* **`customParameterName`**

   La valeur de cette propriété est `customParameterValue`.

   * Type de propriété : Chaîne
   * Cette propriété n’est **pas** requise.


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

* Voici la configuration du fichier landingPage.xml.js :

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Si la demande de Cible aboutit et que le contenu de votre offre est renvoyé, votre page se traduira par :

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Si le serveur de Cible ne peut pas être atteint ou si la demande expire, votre page se traduira par :

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

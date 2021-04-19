---
description: Vous pouvez orienter les utilisateurs vers une destination donnée selon que l’application est installée sur leur appareil (lien profond d’application) ou non (orientation vers un site Web ou une boutique d’applications).
keywords: mobile
seo-description: Vous pouvez orienter les utilisateurs vers une destination donnée selon que l’application est installée sur leur appareil (lien profond d’application) ou non (orientation vers un site Web ou une boutique d’applications).
seo-title: Spots
solution: Experience Cloud,Analytics
title: Spots
topic-fix: Metrics
uuid: 7dce8ab2-2a5d-4384-ac1e-e31dfaa33654
exl-id: b6d4588f-4f28-4c1b-9291-f4b9154d84f7
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 100%

---

# Spots {#interstitials}

Vous pouvez orienter les utilisateurs vers une destination donnée selon que l’application est installée sur leur appareil (lien profond d’application) ou non (orientation vers un site Web ou une boutique d’applications). Il est préférable de laisser aux utilisateurs le choix du routage. Les marketeurs peuvent offrir des choix aux utilisateurs en configurant une page de spot qui présente aux utilisateurs les destinations disponibles.

Pour configurer un spot en  créant un lien marketing :

1. Cliquez sur **[!UICONTROL Modifier le spot de lien profond]**.

   ![Spot de lien profond](assets/interstitial2.png)

1. Renseignez les champs suivants :

   * **[!UICONTROL HTML personnalisé]**

      Sélectionnez votre page HTML de spots personnalisés.

      En utilisant des spots personnalisés, les marketeurs peuvent personnaliser les pages d’entrée de spots à l’aide de code HTML/CSS/JS personnalisé, ce qui vous permet de personnaliser vos pages.

      Voici les conditions requises pour la page HTML :

      * Doit être un fichier HTML.
      * Doit contenir les espaces réservés `%%DEST%%` et `%%FALLBACK%%`.
      * Le code HTML chargé sera affiché dans un `<iframe>`.

         Vous devez vous assurer que les cibles de vos liens pointent vers une fenêtre parente. Vous pouvez inclure `<base target="_parent" />` dans `<head>` ou spécifier une propriété cible pour chaque `<a/>`.

         >[!TIP]
         >
         >Si vous chargez du code HTML personnalisé, les quatre autres options de ce tableau ne seront pas utilisées, sauf si vous supprimez le fichier chargé.
   * **[!UICONTROL URL d’image]**

      Spécifiez l’URL vers un fichier image.

   * **[!UICONTROL Corps de texte]**

      Spécifiez le corps du texte du spot.

   * **[!UICONTROL Confirmer le texte]**

      Spécifiez le texte du bouton.

   * **[!UICONTROL Texte de rechange]**

      Spécifiez le texte de rechange à afficher.

      Ce champ met à jour le bouton de texte en cas d’échec d’un lien profond. Les utilisateurs sont invités à cliquer sur le lien profond avant d’être dirigés vers une option de substitution. Par exemple, une boutique d’applications peut être utilisée pour télécharger et installer l’application ou pour diriger les utilisateurs vers le site Web de la société. Le texte de rechange indique aux utilisateurs qu’il existe une autre option en cas d’échec du lien profond.


1. (**Facultatif**) Cliquez sur les icônes au-dessus de l’image afin d’avoir un aperçu du spot pivoté sur différents appareils.

   Vous pouvez modifier l’image en dehors de Mobile Services afin d’être sûr qu’elle s’affiche correctement dans différentes situations.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

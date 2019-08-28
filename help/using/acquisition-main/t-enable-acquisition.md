---
description: Le suivi des acquisitions doit être activé dans la configuration du SDK avant de pouvoir effectuer un suivi et un rapport sur les liens marketing.
keywords: mobile
seo-description: Le suivi des acquisitions doit être activé dans la configuration du SDK avant de pouvoir effectuer un suivi et un rapport sur les liens marketing.
seo-title: Configuration d’Acquisition
solution: Marketing Cloud, Analytics
title: Configuration d’Acquisition
topic: Mesures
uuid: e 996 e 43 e -8 a 77-47 a 3-a 6 fb -53 f 676 f 92 bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configuration d’Acquisition {#configure-acquisition}

Le suivi des acquisitions doit être activé dans la configuration du SDK avant de pouvoir effectuer un suivi et un rapport sur les liens marketing.

1. Sur la page Gérer les paramètres de l’application de l’application, accédez à la section **[!UICONTROL Options d’acquisition du SDK.]**
1. Exécutez les tâches ci-après :

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Entrez une valeur dans le champ Délai **[!UICONTROL d'expiration du référent (secondes)]** .

      (**Facultatif**) Si vous activez la case **[!UICONTROL à]** cocher Activer, ce champ est facultatif. Vous pouvez modifier la valeur de délai d’expiration, exprimée en secondes. Ce paramètre spécifie la période d'attente des informations d'acquisition avant d'envoyer le premier accès au lancement.
   >[!IMPORTANT]
   >Vous devez entrer une valeur non nulle. Si vous activez l'acquisition mais laissez la valeur comme zéro, les liens d'acquisition ne fonctionneront pas. Nous vous recommandons d'utiliser la valeur par défaut de 5 secondes.

1. Téléchargez et utilisez le nouveau fichier de configuration du SDK dans votre application.

   Vous avez correctement configuré Acquisition sur **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).

---
description: Le suivi des acquisitions doit être activé dans la configuration du SDK avant que vous puissiez effectuer le suivi et créer des rapports sur les liens marketing.
keywords: mobile
seo-description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
seo-title: Configuration d’Acquisition
solution: Marketing Cloud,Analytics
title: Configuration d’Acquisition
topic: Mesures
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configuration d’Acquisition {#configure-acquisition}

Le suivi des acquisitions doit être activé dans la configuration du SDK avant que vous puissiez effectuer le suivi et créer des rapports sur les liens marketing.

1. Sur la page Gérer les paramètres de l’application de l’application, accédez à la section **[!UICONTROL Options d’acquisition du SDK.]**
1. Exécutez les tâches ci-après :

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Entrez une valeur dans le champ Délai d’expiration du **[!UICONTROL référent (secondes)]** .

      (**Facultatif**) Si vous avez activé la case à cocher **[!UICONTROL Activer]** , ce champ est facultatif. Vous pouvez modifier la valeur de délai d’expiration, exprimée en secondes. Ce paramètre spécifie la période d’attente des informations d’acquisition avant l’envoi de l’accès au premier lancement.
   >[!IMPORTANT]
   >Vous devez entrer une valeur non nulle. Si vous activez l’option Acquisition mais que la valeur reste zéro, les liens d’acquisition ne fonctionneront pas. Nous vous recommandons d’utiliser la valeur par défaut de 5 secondes.

1. Téléchargez et utilisez le nouveau fichier de configuration du SDK dans votre application.

   Vous avez correctement configuré Acquisition sur **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).

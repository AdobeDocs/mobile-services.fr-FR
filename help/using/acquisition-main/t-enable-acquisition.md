---
description: Pour que vous puissiez effectuer un suivi des liens marketing et générer des rapports, le suivi d’acquisition doit être activé dans la configuration du SDK.
keywords: mobile
seo-description: Pour que vous puissiez effectuer un suivi des liens marketing et générer des rapports, le suivi d’acquisition doit être activé dans la configuration du SDK.
seo-title: Configuration d’Acquisition
solution: Experience Cloud,Analytics
title: Configuration d’Acquisition
topic: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 100%

---


# Configuration d’Acquisition {#configure-acquisition}

Pour que vous puissiez effectuer un suivi des liens marketing et générer des rapports, le suivi d’acquisition doit être activé dans la configuration du SDK.

1. Sur la page Gérer les paramètres de l’application de l’application, accédez à la section **[!UICONTROL Options d’acquisition du SDK.]**
1. Exécutez les tâches ci-après :

   * Pour activer Acquisition, cochez la case **[!UICONTROL Activer]**.

      Lorsque vous cochez cette case, le champ **[!UICONTROL Délai d’expiration du référent]** devient actif, et la valeur passe de 0 à 5.

   * Saisissez une valeur dans le champ **[!UICONTROL Délai d’expiration du référent (secondes)]**.

      (**Facultatif**) Si vous avez activé la case à cocher **[!UICONTROL Activer]**, ce champ est facultatif. Vous pouvez modifier la valeur de délai d’expiration, exprimée en secondes. Cette valeur détermine la période d’attente des informations d’Acquisition avant l’envoi de la correspondance du premier lancement.
   >[!IMPORTANT]
   >Vous devez saisir une valeur non nulle. Si vous activez Acquisition, mais laissez la valeur de délai d’expiration sur zéro, les liens Acquisition ne fonctionneront pas. Nous vous recommandons d’utiliser la valeur par défaut de 5 secondes.

1. Téléchargez et utilisez le nouveau fichier de configuration du SDK dans votre application.

   Vous avez correctement configuré Acquisition sur **iOS**. 
Pour activer Acquisition sur **Android**, effectuez les étapes indiquées dans la section [Suivi d’acquisition mobile](/help/android/acquisition-main/acquisition.md).

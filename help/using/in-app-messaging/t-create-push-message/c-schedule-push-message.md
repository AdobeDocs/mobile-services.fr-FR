---
description: Dans l’interface utilisateur d’Adobe Mobile Services, vous pouvez planifier la diffusion immédiate d’un message push, la diffusion ultérieure et la diffusion récurrente. Ces événements peuvent être planifiés sur une base quotidienne, hebdomadaire ou mensuelle.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 'Planification : message push'
topic-fix: Metrics
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
exl-id: 36f263a0-4aad-423e-bb78-9c532c98df19
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 100%

---

# Planification : messages push {#schedule-push-message}

Dans l’interface utilisateur d’Adobe Mobile Services, vous pouvez planifier la diffusion immédiate d’un message push, la diffusion ultérieure et la diffusion récurrente. Ces événements peuvent être planifiés sur une base quotidienne, hebdomadaire ou mensuelle.

>[!TIP]
>
>Les utilisateurs peuvent, à tout moment, modifier les paramètres de programmation pour une tâche de messages push. Si aucune date applicable n’est définie pour l’envoi d’un message récurrent (par exemple une tâche mensuelle récurrente tous les 31 du mois, le 31 février ou le cinquième jeudi du mois), aucun message n’est envoyé.

À noter :

* Le format de date et d’heure approprié est `hh:mm` et `mm/dd/yyyy`.

* Vous pouvez modifier un message programmé des façons suivantes :

   * Repousser à une date ultérieure.
   * Remplacer l’intervalle de répétition par un autre intervalle.

      Si, par exemple, vous aviez à l’origine un message qui était envoyé tous les jours, vous pouvez passer à la fréquence hebdomadaire.

## Avant de planifier des messages push récurrents

Vous **devez** comprendre les informations suivantes avant de programmer l’envoi de messages push récurrents :

* Les options affichées dans la liste déroulante **[!UICONTROL Répétition]** dépendent de la date que vous avez saisie ou sélectionnée.

   Par exemple, si vous avez tapé `Saturday, October 7`, les options suivantes s’affichent :

   * **[!UICONTROL Jamais]**
   * **[!UICONTROL Chaque jour]**
   * **[!UICONTROL Chaque samedi]**
   * **[!UICONTROL Le 7 de chaque mois]**
   * **[!UICONTROL Le 1er samedi de chaque mois]**

* Les messages push sont programmés et envoyés selon le temps universel coordonné (Greenwich Mean Time).

   Par exemple, si vous avez planifié l’envoi d’un message récurrent tous les samedis à 12h00 (midi) **PST**, à partir du 7 octobre, le message sera en fait envoyé le samedi à 19h00 **GMT**.
* Les messages ne sont pas envoyés de la même façon selon que vous vous trouvez aux États-Unis, en Europe ou en Asie.

   Par exemple, si vous vous trouvez à San Jose, en Californie, et que vous planifiez l’envoi d’un message le ***31 octobre*** à 17h30 **PST**, le message est en fait envoyé le ***1er novembre*** à 12h30 **GMT.** Si vous vous trouvez à Tokyo, et que vous programmez l’envoi d’un message le ***1er janvier*** à 5h30 du matin, il sera envoyé le ***31 décembre*** à 20h30 **GMT**.
* Les messages push sont envoyés une heure plus tôt ou plus tard, en fonction de l’heure d’hiver et de l’heure d’été.
* Lorsque vous consultez votre rapport des messages push, le message s’affiche dans le fuseau horaire local de votre système.

   Par exemple, si l’heure de début est 12h00 (**PST**), bien que le message soit envoyé à 19h **GMT**, le rapport de messages affiche 12h00 (**PST**) comme heure d’envoi.

## Planification d’un message push récurrent {#section_675BD754E5A04423A1751193698A978F}

1. Sur la page Planification d’un nouveau message push, sélectionnez **[!UICONTROL Planifié]** ou **[!UICONTROL Maintenant]**.

   Pour plus d’informations, voir [Création d’un message push](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   Si vous avez sélectionné **[!UICONTROL Maintenant]**, le message est envoyé immédiatement. Afin d’éviter l’envoi immédiat d’un message, cliquez sur **[!UICONTROL Enregistrer en tant que brouillon]**.

   ![](assets/schedule-push-message.png)

1. Si vous sélectionnez **[!UICONTROL Planifié]**, cliquez sur l’icône de calendrier, puis sélectionnez ou saisissez une date de début.
1. Tapez une heure. 
1. Dans **[!UICONTROL Répéter]**, sélectionnez l’une des options suivantes :

   * **[!UICONTROL Jamais]**
   * **[!UICONTROL Chaque jour]**
   * **[!UICONTROL Chaque mardi]**
   * **`<Day x>`du mois**

      Les options affichées changent en fonction du jour sélectionné ou saisi comme jour de début.
   * **`<nth day>`de chaque mois**

      La valeur affichée change en fonction de la date que vous avez sélectionnée ou saisie comme date de début.

1. Dans **[!UICONTROL Fin de répétition]**, saisissez une date et une heure de fin.
1. Cliquez sur l’une des options suivantes :

   * **[!UICONTROL Enregistrer en tant que brouillon]**

      Cette option enregistre le message sous la forme de brouillon. Vous pouvez sélectionner cette option pour enregistrer un message qui est inachevé ou afin qu’une autre personne puisse le modifier et l’approuver avant de l’activer.

      Si vous avez sélectionné **[!UICONTROL Maintenant]** à l’étape précédente, le projet de message est envoyé immédiatement lors de son activation. Si vous avez sélectionné la date et l’heure de diffusion du message, celui-ci est envoyé à l’horaire désigné.

   * **[!UICONTROL Enregistrement et planification]**

      Cette option envoie le message le jour et l’heure planifiés.

Pour envoyer le brouillon de message ultérieurement, effectuez l’une des tâches suivantes :

* Cliquez sur **[!UICONTROL Gestion des messages]**, sélectionnez la case à cocher à côté du message, puis cliquez sur **[!UICONTROL Activer la sélection]**.
* Cliquez sur **[!UICONTROL Enregistrer et envoyer]** pour enregistrer le message et l’envoyer.

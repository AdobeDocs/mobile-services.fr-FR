---
description: Vous pouvez configurer les options du SDK Analytics sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Configuration des options du SDK Analytics
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%

---

# Configuration des options du SDK Analytics {#configure-sdk-analytics-options}

{#eol}

Vous pouvez configurer les options du SDK Analytics sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.

Renseignez les champs suivants sous les **[!UICONTROL Options du SDK Analytics]** :

* **[!UICONTROL Utiliser HTTPS]**

   Activez le protocole HTTPS pour une sécurité renforcée.

* **[!UICONTROL Accès rétroactifs à la session]**

   Activez ou désactivez la capacité qu’a le SDK Adobe d’antidater les correspondances avec les informations de session. Les correspondances avec les informations de session se composent actuellement des blocages et de la durée des sessions. Lorsqu’il est activé, le SDK Adobe antidate l’accès aux informations de session à 1 seconde après le dernier accès de la session précédente. Cela signifie que les blocages et les données de session seront corrélés avec la date correcte à laquelle ils se sont produits. Un accès est antidaté à chaque nouveau lancement de l’application. Lorsque l’option est désactivée, le SDK Adobe rattache les informations de session au cycle de vie en cours.

* **[!UICONTROL Confidentialité]**

   Sélectionnez une option de confidentialité :

   * **[!UICONTROL Envoyer les données jusqu’à exclusion]**
   * **[!UICONTROL Conserver les données jusqu’à souscription]**

* **[!UICONTROL Délai d’expiration de la session (secondes)]**

   Spécifiez la valeur du délai d’expiration de la session.

   Le délai par défaut est de 300 secondes. Spécifie la durée, en secondes, qui doit s’écouler entre le lancement de l’application et le moment où le lancement est considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque votre application est envoyée en arrière-plan et réactivée. Le temps passé par votre application en arrière-plan n’est pas inclus dans la durée de session.

* **[!UICONTROL Limite de lot]**

   Spécifiez le nombre de correspondances en file d’attente souhaitées avant d’envoyer les données.

   La définition de la valeur 0 envoie les correspondances immédiatement. La limite de lot représente le nombre limite d’accès pouvant faire l’objet d’appels consécutifs. Si, par exemple, cette option est définie sur 10, chaque accès précédant le 10e accès est placé en file d’attente. Lorsque le 10e accès intervient, les 10 accès sont tous envoyés consécutivement.

* **[!UICONTROL Plus de détails]**

   Cliquez sur le lien **[!UICONTROL Plus de détails]** pour afficher l’identifiant de la suite de rapports et le serveur de suivi, activer ou désactiver le suivi hors ligne et afficher le modèle d’encodage de caractères utilisé (par exemple, UTF-8).

   Lorsque le suivi hors ligne est activé, les données générées par l’appareil pendant qu’il est hors ligne sont horodatées et envoyées ultérieurement. Si cette option est désactivée, les données hors ligne sont ignorées.

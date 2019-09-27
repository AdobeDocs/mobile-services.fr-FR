---
description: Vous pouvez configurer les options du SDK Analytics sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
keywords: mobile
seo-description: Vous pouvez configurer les options du SDK Analytics sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.
seo-title: Configuration des options du SDK Analytics
solution: Marketing Cloud,Analytics
title: Configuration des options du SDK Analytics
topic: Mesures
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

Vous pouvez configurer les options du SDK Analytics sur la page Gérer les paramètres de l’application lors de la création d’une application ou de la modification d’une application existante.

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL Utiliser HTTPS]**

   Activez le protocole HTTPS pour une sécurité renforcée.

* **[!UICONTROL Accès rétroactifs à la session]**

   Activez ou désactivez la possibilité pour le SDK Adobe d’antidater les accès aux informations de session. Les correspondances avec les informations de session se composent actuellement des blocages et de la durée des sessions. Lorsque l’option est activée, le kit SDK Adobe crée un accès rétroactif aux informations de session à raison de 1 seconde après la dernière correspondance intervenue dans la session qui précède. Ceci signifie que les données de blocage et de session sont corrélées avec la date correcte à laquelle ces événements se sont produits. Un accès est antidaté à chaque nouveau lancement de l’application. Lorsque l’option est désactivée, le SDK Adobe rattache les informations de session au cycle de vie en cours.

* **[!UICONTROL Confidentialité]**

   Sélectionnez une option de confidentialité :

   * **[!UICONTROL Envoyer les données jusqu’à exclusion]**
   * **[!UICONTROL Conserver les données jusqu’à souscription]**

* **[!UICONTROL Délai d’expiration de la session (secondes)]**

   Spécifiez la valeur du délai d’expiration de la session.

   Le délai par défaut est de 300 secondes. Spécifie la durée, en secondes, qui doit s’écouler entre les lancements de l’application pour qu’un lancement soit considéré comme une nouvelle session. Ce délai d’attente s’applique également lorsque l’application est placée en arrière-plan et réactivée. La durée passée en arrière-plan n’est pas prise en compte dans la durée de la session.

* **[!UICONTROL Limite de lot]**

   Spécifiez le nombre de correspondances en file d’attente souhaitées avant d’envoyer les données.

   La définition de la valeur 0 envoie les correspondances immédiatement. La limite de lot représente le seuil du nombre de visites à envoyer sous forme d’appels consécutifs. Si cette option est par exemple définie sur 10, chaque correspondance précédant la 10e correspondance est enregistrée en file d’attente. Lorsque la 10e correspondance intervient, les 10 correspondances sont toutes envoyées consécutivement.

* **[!UICONTROL Plus de détails]**

   Cliquez sur le lien **[!UICONTROL Plus de détails]pour afficher l’identifiant de la suite de rapports et le serveur de suivi, activer ou désactiver le suivi hors ligne et afficher le modèle d’encodage de caractères utilisé (par exemple, UTF-8).**

   Lorsque le suivi hors ligne est activé, les données générées par le périphérique en mode hors ligne sont horodatées et envoyées ultérieurement. Si cette option est désactivée, les données hors ligne sont ignorées.

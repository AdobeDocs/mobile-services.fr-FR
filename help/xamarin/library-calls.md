---
description: Informations pour vous aider à lancer des appels au module externe à partir de vos scripts.
keywords: Xamarin
solution: Experience Cloud
title: Appels à la bibliothèque
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# Appels à la bibliothèque{#making-calls-to-the-library}

Ces informations vous aident à lancer des appels au module externe à partir de vos scripts.

Pour lancer des appels au module externe à partir de vos scripts, vous devez importer l’espace de noms .

En utilisant `Com.Adobe.Mobile` :

* **iOS** : Après avoir importé l’espace de noms, vous pouvez lancer des appels directement au SDK via les méthodes statiques dans les  `ADBMobile` classes.

* **Android** : Vous pouvez effectuer des appels directement au SDK via les méthodes statiques dans les  `Config/Analytics/Target/AudienceManager/Media`classes.

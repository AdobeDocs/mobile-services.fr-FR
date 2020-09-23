---
description: Informations destinées à vous aider à appeler le module externe à partir de vos scripts.
keywords: Xamarin
seo-description: Informations destinées à vous aider à appeler le module externe à partir de vos scripts.
seo-title: Appels à la bibliothèque
solution: Experience Cloud
title: Appels à la bibliothèque
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 13%

---


# Appels à la bibliothèque{#making-calls-to-the-library}

Ces informations vous aident à appeler le module externe à partir de vos scripts.

Pour appeler le module externe à partir de vos scripts, vous devez importer l’espace de nommage.

En utilisant `Com.Adobe.Mobile`:

* **iOS**: Après avoir importé l’espace de nommage, vous pouvez invoquer directement le SDK au moyen des méthodes statiques des `ADBMobile` classes.

* **Android**: Vous pouvez appeler directement le SDK au moyen des méthodes statiques des `Config/Analytics/Target/AudienceManager/Media`classes.


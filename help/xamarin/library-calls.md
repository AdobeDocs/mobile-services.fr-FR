---
description: Informations relatives à l’appel du module externe à partir des scripts.
keywords: Xamarin
seo-description: Informations relatives à l’appel du module externe à partir des scripts.
seo-title: Appels à la bibliothèque
solution: Marketing Cloud,Développeur
title: Appels à la bibliothèque
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

Ces informations vous aident à appeler le module externe à partir de vos scripts.

Pour lancer des appels au module externe depuis vos scripts, vous devez importer l’espace de noms.

By using :`Com.Adobe.Mobile`

* **iOS**: Après avoir importé l’espace de noms, vous pouvez invoquer directement le SDK au moyen des méthodes statiques des `ADBMobile` classes.

* **Android**: Vous pouvez appeler directement le SDK via les méthodes statiques des `Config/Analytics/Target/AudienceManager/Media`classes.


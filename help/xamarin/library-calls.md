---
description: Informations relatives à l’appel du module externe à partir des scripts.
keywords: Xamarin
seo-description: Informations relatives à l’appel du module externe à partir des scripts.
seo-title: Appels à la bibliothèque
solution: Marketing Cloud, développeur
title: Appels à la bibliothèque
uuid: a 480201 a -4090-4662-8 dd 8-56 f 62144 cd 93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

Ces informations vous aident à effectuer des appels au module externe à partir de vos scripts.

Pour lancer des appels au module externe depuis vos scripts, vous devez importer l’espace de noms.

En utilisant `Com.Adobe.Mobile`:

* **Ios**: Après avoir importé l'namespace de noms, vous pouvez invoquer directement le kit SDK via les méthodes statiques des `ADBMobile` classes.

* **Android**: Vous pouvez invoquer directement le SDK au moyen des méthodes statiques des `Config/Analytics/Target/AudienceManager/Media`classes.


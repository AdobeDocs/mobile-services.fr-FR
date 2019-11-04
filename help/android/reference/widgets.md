---
description: Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que dans votre application. Les widgets et l’application partagent le même contexte d’application, de manière à ce que l’ordre d’accès et l’identification des visiteurs soient conservés.
keywords: android;library;mobile;sdk
seo-description: Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que dans votre application. Les widgets et l’application partagent le même contexte d’application, de manière à ce que l’ordre d’accès et l’identification des visiteurs soient conservés.
seo-title: Widgets Android
solution: Experience Cloud,Analytics
title: Widgets Android
topic: Développeur et mise en œuvre
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Widgets Android {#android-widgets}

Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que dans votre application. Les widgets et l’application partagent le même contexte d’application, de manière à ce que l’ordre d’accès et l’identification des visiteurs soient conservés.

Les recommandations suivantes vous aideront à effectuer le suivi des widgets Android :

* Ne mettez pas en œuvre d’appels de mesures de cycle de vie ( `startActivity`/ `stopActivity`) dans le widget.

* Afin d’être informé lorsqu’un widget est ajouté à l’écran d’accueil, ajoutez un appel `trackState` ou `trackEvent` à la méthode `onEnabled` du widget.

* Afin d’être informé lorsqu’une application est lancée à partir d’un widget, ajoutez un appel `trackState` ou `trackEvent` avant de lancer votre application.

* Pour effectuer le suivi du contexte d’une action, vous pouvez définir une variable `ContextData` qui offre l’option de segmenter chaque action séparément (par exemple, `AppExperienceType="widget"` et `app`).


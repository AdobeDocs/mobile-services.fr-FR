---
description: Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que votre application. Les widgets partagent le contexte de l’application avec votre application, de sorte que l’ordre d’accès et l’identification du visiteur sont préservés.
keywords: android;library;mobile;sdk
seo-description: Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que votre application. Les widgets partagent le contexte de l’application avec votre application, de sorte que l’ordre d’accès et l’identification du visiteur sont préservés.
seo-title: Widgets Android
solution: Experience Cloud,Analytics
title: Widgets Android
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '179'
ht-degree: 100%

---


# Widgets Android {#android-widgets}

Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que votre application. Les widgets partagent le contexte de l’application avec votre application, de sorte que l’ordre d’accès et l’identification du visiteur sont préservés.

Les instructions suivantes vous aideront à effectuer le suivi des widgets Android :

* Ne mettez pas en œuvre d’appels de mesures de cycle de vie ( `startActivity`/ `stopActivity`) dans le widget.

* Afin d’être informé lorsqu’un widget est ajouté à l’écran d’accueil, ajoutez un appel `trackState` ou `trackEvent` à la méthode `onEnabled` du widget.

* Afin d’être informé lorsqu’une application est lancée à partir d’un widget, ajoutez un appel `trackState` ou `trackEvent` avant de lancer votre application.

* Pour effectuer le suivi du contexte d’une action, vous pouvez définir une variable `ContextData` qui offre l’option de segmenter chaque action séparément (par exemple, `AppExperienceType="widget"` et `app`).


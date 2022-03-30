---
description: Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que votre application. Les widgets partagent le contexte de l’application avec votre application, de sorte que l’ordre d’accès et l’identification du visiteur sont préservés.
keywords: android;library;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Widgets Android
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Widgets Android {#android-widgets}

Les widgets Android peuvent être suivis en utilisant les mêmes méthodes que votre application. Les widgets partagent le contexte de l’application avec votre application, de sorte que l’ordre d’accès et l’identification du visiteur sont préservés.

Les instructions suivantes vous aideront à effectuer le suivi des widgets Android :

* Ne mettez pas en œuvre d’appels de mesures de cycle de vie ( `startActivity`/ `stopActivity`) dans le widget.

* Afin d’être informé lorsqu’un widget est ajouté à l’écran d’accueil, ajoutez un appel `trackState` ou `trackEvent` à la méthode `onEnabled` du widget.

* Afin d’être informé lorsqu’une application est lancée à partir d’un widget, ajoutez un appel `trackState` ou `trackEvent` avant de lancer votre application.

* Pour effectuer le suivi du contexte d’une action, vous pouvez définir une variable `ContextData` qui offre l’option de segmenter chaque action séparément (par exemple, `AppExperienceType="widget"` et `app`).

---
description: Les informations suivantes expliquent comment rediriger un lien de campagne d’acquisition héritée basé sur l’empreinte numérique d’un périphérique.
seo-description: Les informations suivantes expliquent comment rediriger un lien de campagne d’acquisition héritée basé sur l’empreinte numérique d’un périphérique.
seo-title: Test de l’acquisition héritée
solution: Experience Cloud,Analytics
title: Test de l’acquisition héritée
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '272'
ht-degree: 100%

---


# Test de l’acquisition héritée {#testing-legacy-acquisition}

Les informations suivantes expliquent comment rediriger un lien de campagne d’acquisition héritée basé sur l’empreinte numérique d’un périphérique.

Si l’application mobile n’est pas encore sur Google Play, vous pouvez sélectionner n’importe quelle destination lors de la création du lien de campagne. Cela a uniquement une incidence sur l’application utilisée par le serveur pour vous rediriger lorsque vous cliquez sur le lien d’acquisition. Le lien d’acquisition pourra toujours être testé.

1. Accédez à **[!UICONTROL Utilisation de liens d’acquisition hérités]** dans Adobe Mobile Services et créez une URL de campagne d’acquisition.

   Pour plus d’informations, voir [Utilisation de liens d’acquisition hérités](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Cliquez sur le lien créé avec le périphérique mobile sur lequel l’application sera installée.

   Les serveurs d’Adobe (`c00.adobe.com`) enregistrent l’empreinte numérique puis vous redirigent vers l’App Store. Il n’est pas nécessaire de télécharger l’application pour effectuer les tests.

1. Lancez l’application pour la première fois à partir du même périphérique mobile que celui utilisé à l’étape 2.

   Pour vous assurer d’effectuer correctement l’opération, supprimez puis réinstallez l’application.

À noter :

* Le serveur d’acquisition fournit une correspondance d’attribution basée sur l’adresse IP et les informations agent-utilisateur enregistrées lorsque vous cliquez sur le lien (étape 2) et lors du lancement de l’application (étape 3).
* En utilisant des outils de surveillance HTTP, les accès envoyés à partir de l’application peuvent être contrôlés pour vérifier l’attribution d’acquisition.

>[!TIP]
>
>Des variations dans l’agent-utilisateur envoyé peuvent provoquer l’échec de l’attribution.

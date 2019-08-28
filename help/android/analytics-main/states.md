---
description: Les états correspondent aux différents écrans ou affichages de votre application.
seo-description: Les états correspondent aux différents écrans ou affichages de votre application.
seo-title: Suivi des états de l’application
solution: Marketing Cloud, Analytics
title: Suivi des états de l’application
topic: Développeur et mise en œuvre
uuid: 69 c 99 d 05-5816-4 c 86-97 c 5-d 218 dc 26 c 129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Suivi des états d’application {#track-app-states}

Les états correspondent aux différents écrans ou affichages de votre application.

Chaque fois qu’un nouvel état s’affiche dans votre application (par exemple, lorsqu’un utilisateur navigue de la page d’accueil vers le fil d’actualité), un appel `trackState` est envoyé. Dans Android, `trackState` est généralement appelé chaque fois qu’une nouvelle activité est chargée.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Ajoutez la bibliothèque à votre projet et mettez en œuvre le cycle de vie.

   Pour plus d'informations, voir *Ajout du SDK et du fichier Config à votre projet intellij IDEA ou Eclipse* dans [l'implémentation principale et le cycle de vie](/help/android/getting-started/dev-qs.md).

1. Importez la bibliothèque :

   ```java
   import com.adobe.mobile.*;
   ```

1. Dans la fonction `onCreate`, appelez `trackState` pour envoyer un accès correspondant à l’affichage d’état suivant :

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces, `View State` is reported as `Page Name`, and `state views` is reported as `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

Les valeurs de données contextuelles doivent être mappées à des variables personnalisées dans Adobe Mobile Services :

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Les états sont généralement affichés en utilisant un rapport de cheminement qui permet de voir comment les utilisateurs naviguent dans votre application, ainsi que les états les plus fréquemment affichés.

|  |  |
|--- |--- |
| Adobe Mobile Services   | Rapport **[!UICONTROL Afficher les états.]** Ce rapport est basé sur les chemins que les utilisateurs prennent dans votre application. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics  | Vous pouvez consulter les états sur les différents affichages des Pages : rapport **Pages**, rapport **[!UICONTROL Pages vues]** et rapport **Chemin[!UICONTROL .]** |
| Analyses ad hoc | Vous pouvez consulter les états sur les différents affichages des Pages au moyen de la dimension **Page**, de la mesure **[!UICONTROL Pages vues]** et des rapports **Chemin[!UICONTROL .]** |



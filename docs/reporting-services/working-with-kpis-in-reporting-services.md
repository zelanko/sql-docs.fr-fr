---
title: "Utilisation des indicateurs de performance cl&#233;s dans Reporting Services | Microsoft Docs"
ms.date: "02/24/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a28cf500-6d47-4268-a248-04837e7a09eb
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 8
---
# Utilisation des indicateurs de performance cl&#233;s dans Reporting Services
Un indicateur de performance clé (KPI) est un indice visuel qui représente la progression vers un objectif.  Les Indicateurs de performance clés sont utiles pour les équipes, les responsables et les entreprises pour évaluer rapidement l’état d’avancement par rapport à des objectifs mesurables.   
  
À l’aide des indicateurs de performance clés dans SQL Server 2016 Reporting Services, vous pouvez facilement visualiser les réponses aux questions suivantes :  
  
-   Suis-je en avance ou en retard ?  
  
-   Quelle est mon avance ou quel est mon retard ?  
  
-   Quelle est la quantité minimum de travail que j’ai terminé ?  
  
## Création d’un dataset  
Un indicateur de performance clé utilise uniquement la première ligne de données issue d’un dataset partagé. Assurez-vous que les données que vous souhaitez utiliser se trouvent sur cette première ligne. Pour créer un dataset partagé, vous pouvez utiliser le Générateur de rapports ou SQL Server Data Tools.  
  
> **Remarque** : le dataset ne doit pas nécessairement être dans le même dossier que l’indicateur de performance clé.  
  
## Positionnement des indicateurs de performance clés  
  
Les indicateurs de performance clés peuvent être créés dans n’importe quel dossier sur votre serveur de rapports.  Avant de créer un indicateur de performance clé, vous devez réfléchir au meilleur emplacement pour celui-ci. Il est préférable de le placer dans un dossier visible pour les utilisateurs, qui soit en même temps utile à d’autres rapports et indicateurs de performance clés.  
  
## Ajout d’un indicateur de performance clé  
  
Après avoir déterminé l’emplacement de votre indicateur de performance clé, accédez à ce dossier et sélectionnez **Nouveau** > **Indicateur de performance clé** dans le menu supérieur.  
  
![rsCreateKPI1](../reporting-services/media/rscreatekpi1.png)  
  
L’écran **Nouvel indicateur de performance clé** s’affiche.  
  
![rsCreateKPI2](../reporting-services/media/rscreatekpi2.png)  
  
Vous pouvez assigner des valeurs statiques ou utiliser les données issues d’un dataset partagé. Lorsque vous créez un indicateur de performance clé, il est rempli avec une série aléatoire de données manuelles.  
  
|Champ|Description|  
|---|---|  
|Format de la valeur|  Permet de modifier le format de la valeur affichée.|   
|Value|La valeur à afficher pour l’indicateur de performance clé.|  
|Objectif|Utilisé en comparaison à une valeur numérique et présenté sous forme de différence de pourcentage.|  
|État|Valeur numérique utilisée pour déterminer la couleur de vignette de l’indicateur de performance clé. Les valeurs valides sont 1 (vert), 0 (orange) et -1 (rouge).|  
|Ensemble de tendances|Valeurs numériques séparées par des virgules utilisées pour la visualisation de graphique. Ceci peut également être défini sur une colonne d’un dataset avec des valeurs qui représentent la tendance.|  
  
> **Avertissement** : bien que vous pouvez utiliser la valeur texte pour le champ **État** au moment de la conception, vous devez utiliser la valeur numérique en cas d’actualisation d’un dataset. Si vous actualisez un dataset avec la valeur texte, au lieu de la valeur numérique, cela peut endommager les indicateurs de performance clés sur votre serveur.  
  
> **Remarque** : les champs **Valeur**, **Objectif** et **État** peuvent uniquement choisir une valeur à partir de la première ligne du résultat d’un dataset. Toutefois, le champ **Ensemble de tendances** peut choisir la colonne qui reflète la tendance.  
  
Procédez comme suit pour utiliser les données d’un dataset partagé.  
  
1.  Modifiez la liste déroulante des champs de **Manuellement** ou **Ne pas définir** à **Champ de dataset**.  
  
    ![rsCreateKPI3](../reporting-services/media/rscreatekpi3.png)  
  
2.  Sélectionnez l’**ellipse (...)** dans la zone de données. L’écran **Choisir un dataset** s’affiche.  
  
    ![rsCreateKPI4](../reporting-services/media/rscreatekpi4.png)  
  
3.  Sélectionnez le dataset qui contient les données que vous souhaitez afficher.  
  
4.  Choisissez le champ que vous souhaitez utiliser. Sélectionnez **OK**.  
  
    ![rsCreateKPI5](../reporting-services/media/rscreatekpi5.png)  
  
5.  Modifiez **Format de la valeur** pour correspondre au format de la valeur. Dans cet exemple, la valeur est une devise.  
  
    ![rsCreateKPI6](../reporting-services/media/rscreatekpi6.png)  
  
6.  Sélectionnez **Appliquer**.  
  
    ![rsCreateKPI7](../reporting-services/media/rscreatekpi7.png)  
  
## Suppression d’un indicateur de performance clé  
  
Pour supprimer un indicateur de performance clé, vous pouvez effectuer les opérations suivantes.  
  
1.  Sélectionnez l’**ellipse (...)** de l’indicateur de performance clé à supprimer. Sélectionnez **Gérer**.  
  
    ![rsRemoveKPI1](../reporting-services/media/rsremovekpi1.png)  
  
2.  Sélectionnez **Supprimer**. Sélectionnez **Supprimer** à nouveau dans la boîte de dialogue de confirmation.  
  
    ![rsRemoveKPI2](../reporting-services/media/rsremovekpi2.png)  
  
## Actualisation d’un indicateur de performance clé  
  
Pour actualiser l’indicateur de performance clé, vous devez configurer un **Plan d’actualisation du cache** pour le dataset partagé. Actuellement, vous ne pouvez pas configurer un plan d’actualisation du cache à partir du portail web. Vous devez utiliser l’ancien Gestionnaire de rapports pour ce faire.   
  
Celui-ci vous guide dans la configuration d’un plan d’actualisation du cache avec certains paramètres de base. Pour plus d’informations sur les plans d’actualisation du cache, consultez [Options d’actualisation du cache (Gestionnaire de rapports)](Cache%20Refresh%20Options%20(Report%20Manager).xml).  
  
1.  Ouvrez le Gestionnaire de rapports et accédez au dataset partagé pour lequel vous voulez configurer les propriétés du plan d’actualisation du cache.   
  
2.  Pointez sur le rapport ou le dataset partagé, puis sélectionnez sur la flèche déroulante.  
  
3.  Dans la liste déroulante, sélectionnez **Gérer**. La page **Propriétés générales** s’affiche.  
  
4.  Sélectionnez l’onglet **Options d’actualisation du cache**.  
  
5.  Pour créer un plan de cache, sélectionnez **Nouveau plan d’actualisation du cache**.  
  
    ![rsRefreshKPI1](../reporting-services/media/rsrefreshkpi1.png)  
  
6.  Vous obtenez un message vous demandant si vous souhaitez activer la mise en cache pour cet élément avec les options par défaut. Sélectionnez **OK**.  
  
    > **Remarque** : vous devez activer et démarrer le service SQL Server Agent pour créer un plan d’actualisation du cache.  
  
7.  Vous pouvez choisir un calendrier spécifique ou un calendrier partagé, le cas échéant.  
  
8.  Les valeurs de l’indicateur de performance clé sont mises à jour lors de l’exécution du calendrier du plan d’actualisation du cache.  
  
    ![rsRefreshKPI2](../reporting-services/media/rsrefreshkpi2.png)  
  
## Voir aussi  
  
- [Portail web (SSRS en mode natif)](../reporting-services/web-portal-ssrs-native-mode.md)  
  
- [Options d'actualisation du cache (Gestionnaire de rapports)](Cache%20Refresh%20Options%20(Report%20Manager).xml)  
  
    
  
  
  

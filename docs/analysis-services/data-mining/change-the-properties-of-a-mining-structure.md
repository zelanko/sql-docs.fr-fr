---
title: "Modifier les propri&#233;t&#233;s d&#39;une structure d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "structures d’exploration de données [Analysis Services], propriétés"
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# Modifier les propri&#233;t&#233;s d&#39;une structure d&#39;exploration de donn&#233;es
  Il existe deux types de propriétés sur une structure d'exploration de données, qui peuvent être modifiées :  
  
-   Propriétés de la structure d'exploration de données qui affectent la structure entière  
  
-   Propriétés sur des colonnes individuelles de la structure  
  
 Notez que certaines propriétés dépendent d'autres paramètres de propriété. Par exemple, vous ne pouvez pas définir les propriétés qui contrôlent le comportement de placement dans un conteneur (notamment <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> ou <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) jusqu’à ce que vous ayez défini le type de données de la colonne sur **Discretized**.  
  
 Pour plus d’informations sur les propriétés de structure d’exploration de données, consultez [Structure d’exploration de données](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### Pour modifier les propriétés d'une structure d'exploration de données  
  
1.  Sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit de la souris sur la structure d’exploration de données ou sur une colonne de la structure d’exploration de données, puis sélectionnez **Propriétés**.  
  
     La fenêtre **Propriétés** s’ouvre dans la partie droite de l’écran si elle n’était pas affichée.  
  
2.  Dans la fenêtre **Propriétés**, sélectionnez la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
## Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
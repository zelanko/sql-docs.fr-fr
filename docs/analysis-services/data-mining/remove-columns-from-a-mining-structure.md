---
title: "Supprimer des colonnes d&#39;une structure d&#39;exploration de donn&#233;es | Microsoft Docs"
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
  - "structures d’exploration de données [Analysis Services], colonnes"
  - "enlèvement de colonnes"
  - "suppression des colonnes"
  - "colonnes [exploration de données], colonnes de structure d’exploration de données"
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 27
---
# Supprimer des colonnes d&#39;une structure d&#39;exploration de donn&#233;es
  Vous pouvez utiliser le Concepteur d'exploration de données pour supprimer des colonnes d'une structure d'exploration de données après que la structure a été créée. Les raisons de la suppression d'une colonne de structure d'exploration de données peuvent inclure les suivantes :  
  
-   La structure d'exploration de données contient plusieurs copies d'une colonne et vous souhaitez éviter l'utilisation de données en double dans un modèle.  
  
-   Les données doivent être protégées, mais l'extraction a été activée.  
  
-   Les données ne sont pas utilisées dans la modélisation et ne doivent pas être traitées.  
  
 La suppression d'une colonne de la structure d'exploration de données ne modifie pas la colonne de la vue de source de données ou dans les données externes ; seules les métadonnées sont supprimées. Toutefois, lorsque vous modifiez les colonnes utilisées dans une structure d'exploration de données, vous devez retraiter la structure et tous les modèles basés sur celle-ci.  
  
### Pour supprimer une colonne d'une structure d'exploration de données  
  
1.  Sélectionnez l’onglet **Structure d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Développez l'arborescence de la structure d'exploration de données pour afficher toutes les colonnes.  
  
3.  Cliquez avec le bouton droit sur la colonne à supprimer, puis sélectionnez **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer les objets**, cliquez sur **OK**.  
  
## Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
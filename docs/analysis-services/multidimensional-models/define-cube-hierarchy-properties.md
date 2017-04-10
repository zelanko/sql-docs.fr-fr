---
title: "D&#233;finir les propri&#233;t&#233;s des hi&#233;rarchies de cube | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hiérarchies [Analysis Services], multiniveau"
  - "hiérarchies [Analysis Services], cubes"
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# D&#233;finir les propri&#233;t&#233;s des hi&#233;rarchies de cube
  Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Activé**|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|**HierarchyID**|Contient l'identificateur unique (ID) de la hiérarchie.|  
|**OptimizedState**|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **FullyOptimized** :<br />                    L'instance construit des index pour la hiérarchie afin d'augmenter les performances en matière de requêtes. Ceci est la valeur par défaut.<br /><br /> **NotOptimized** :<br />                    L'instance ne construit pas d'index supplémentaire.|  
|**Visible**|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est **True**.|  
  
## Voir aussi  
 [Hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
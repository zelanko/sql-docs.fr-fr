---
title: Définir les propriétés d’une hiérarchie de cube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546991"
---
# <a name="define-cube-hierarchy-properties"></a>Définir les propriétés des hiérarchies de cube
  Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`Enabled`|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|`HierarchyID`|Contient l'identificateur unique (ID) de la hiérarchie.|  
|`OptimizedState`|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> `FullyOptimized` : l’instance génère des index pour la hiérarchie afin d’augmenter les performances en matière de requêtes. Il s’agit de la valeur par défaut.<br /><br /> `NotOptimized` : l’instance ne génère pas d’index supplémentaire.|  
|`Visible`|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est `True`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  

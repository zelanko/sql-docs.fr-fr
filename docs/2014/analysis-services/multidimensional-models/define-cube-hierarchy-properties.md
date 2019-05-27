---
title: Définir les propriétés de hiérarchie de Cube | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 0ace708cc4ee09295380b814bbf21f5a1c350974
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66075708"
---
# <a name="define-cube-hierarchy-properties"></a>Définir les propriétés des hiérarchies de cube
  Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`Enabled`|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|`HierarchyID`|Contient l'identificateur unique (ID) de la hiérarchie.|  
|`OptimizedState`|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> `FullyOptimized`: L'instance construit des index pour la hiérarchie afin d'augmenter les performances en matière de requêtes. Valeur par défaut.<br /><br /> `NotOptimized`: L'instance ne construit pas d'index supplémentaire.|  
|`Visible`|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est `True`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  

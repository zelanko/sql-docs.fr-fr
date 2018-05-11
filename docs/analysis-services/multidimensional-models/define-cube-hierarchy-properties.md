---
title: Définir des propriétés de hiérarchie de Cube | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9632719018cf91eebc97b7a56e651bdc3037e5a3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="define-cube-hierarchy-properties"></a>Définir les propriétés des hiérarchies de cube
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété| Description|  
|--------------|-----------------|  
|**Activé**|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|**HierarchyID**|Contient l'identificateur unique (ID) de la hiérarchie.|  
|**OptimizedState**|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **FullyOptimized**:<br />                    L'instance construit des index pour la hiérarchie afin d'augmenter les performances en matière de requêtes. Ceci est la valeur par défaut.<br /><br /> **NotOptimized**:<br />                    L'instance ne construit pas d'index supplémentaire.|  
|**Visible**|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est **True**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies des utilisateurs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  

---
title: Stockage de dimension | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b45ab57b151c2cdab5ae7aa133befd06893037bd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dimensions---storage"></a>Dimensions - stockage
  Dimensions dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent en charge deux modes de stockage :  
  
-   OLAP relationnel (ROLAP)  
  
-   OLAP multidimensionnel (MOLAP)  
  
 Le mode de stockage détermine l'emplacement et le format des données d'une dimension. Le mode de stockage par défaut des dimensions est MOLAP. **Rubriques connexes :**[traitement et Modes de stockage de Partition](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Les données d'une dimension qui utilise MOLAP sont stockées dans une structure multidimensionnelle dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cette structure multidimensionnelle est créée et peuplée lors du traitement de la dimension. Les dimensions MOLAP offrent de meilleures performances d'interrogation que les dimensions ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 Les données d'une dimension qui utilise ROLAP sont stockées dans les tables utilisées pour définir la dimension. Vous pouvez utiliser le mode de stockage ROLAP pour prendre en charge les grandes dimensions sans avoir à dupliquer de grandes quantités de données, mais au prix de performances moindres pour les requêtes. Étant donné que la dimension dépend directement des tables de la vue de source de données utilisée pour la définir, le mode de stockage ROLAP prend également en charge le mode de stockage OLAP en temps réel.  
  
> [!IMPORTANT]  
>  Si une dimension qui utilise le mode ROLAP est incluse dans un cube qui utilise le mode MOLAP, toute modification apportée au schéma dans la table source doit être suivie par le traitement immédiat du cube. Si vous ne procédez pas ainsi, lorsque vous interrogerez le cube, les résultats ne seront pas cohérents. **Rubrique connexe :**[automatiser les tâches Analysis Services d’administration avec SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement et Modes de stockage de partitions](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  

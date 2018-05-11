---
title: Stockage de dimension | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 88b74cedcff7de22e186f4121fdfb3d5a891f030
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="dimensions---storage"></a>Dimensions - stockage
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  

---
title: "Objets (Analysis Services - données multidimensionnelles) de cube | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 018739c4f8da237c1a90a101b96888a8583349be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Objets de cube (Analysis Services - Données multidimensionnelles)
    
## <a name="introducing-cube-objects"></a>Présentation des objets de cube  
 Un objet <xref:Microsoft.AnalysisServices.Cube> simple est composé d'informations de base, de dimensions et de groupes de mesures. Les informations de base incluent le nom du cube, la mesure par défaut du cube, la source de données, le mode de stockage et d'autres informations.  
  
 La collection Dimensions contient le jeu réel de dimensions utilisé dans le cube depuis la collection de dimensions de la base de données. Toutes les dimensions doivent être définies dans la collection de dimensions de la base de données avant d'être référencées dans le cube. Les dimensions privées ne sont pas disponibles dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Les groupes de mesures sont les jeux de mesures du cube. Un groupe de mesures est une collection de mesures qui ont en commun une vue de source de données et un jeu de dimensions. Un groupe de mesures est l'unité du processus pour les mesures ; les groupes de mesures peuvent être traités individuellement, puis parcourus.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|||  
|-|-|  
|Rubrique||  
|[Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Agrégations et conceptions d'agrégation](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Calculs](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Cellules de cube &#40; Analysis Services - données multidimensionnelles &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Programmation du modèle multidimensionnel - propriétés de cube](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Stockage de cube &#40; Analysis Services - données multidimensionnelles &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Traductions de cube](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Relations de dimension](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Indicateurs de performance clés &#40;KPI&#41; dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Mesures et groupes de mesures](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Perspectives](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  


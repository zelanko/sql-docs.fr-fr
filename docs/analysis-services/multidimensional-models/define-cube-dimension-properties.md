---
title: "Définir des propriétés de Dimension de Cube | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6b537ac59e0ca4e680d21cd92cb2f06f34e4adf9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="define-cube-dimension-properties"></a>Définir des propriétés d'une dimension de cube
  Une dimension de cube est une instance d'une dimension de base de données à l'intérieur d'un cube. Une dimension de base de données peut être utilisée dans plusieurs cubes et plusieurs dimensions de cube peuvent être basées sur une seule dimension de base de données. Le tableau suivant décrit les propriétés d'une dimension de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**AllMemberAggregationUsage**|Contrôle la façon dont les agrégations sont conçues par le Concepteur d'agrégation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **Full**: chaque agrégation du cube doit inclure le membre Tous.<br /><br /> **None**: aucune agrégation du cube ne peut inclure le membre Tous. Ceci est la valeur par défaut.<br /><br /> **Unrestricted**: le concepteur d’agrégation ne fait l’objet d’aucune restriction.<br /><br /> **Default**: même fonctionnalité que la valeur Unrestricted.|  
|**Description**|Fournit un nom descriptif pour le niveau.|  
|**DimensionID**|Contient l'identificateur unique (ID) de la dimension de base de données.|  
|**HierarchyUniqueNameStyle**|Détermine comment des noms uniques sont générés pour les hiérarchies qui sont contenues dans la dimension de cube. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **IncludeDimensionName**:<br />                    Le nom de la dimension est inclus dans le nom de la hiérarchie. Ceci est la valeur par défaut.<br /><br /> **ExcludeDimensionName**:<br />                    Le nom de la dimension n'est pas inclus dans le nom de la hiérarchie.|  
|**ID**|Contient l'identificateur unique (ID) de la dimension de cube.|  
|**MemberUniqueNameStyle**|Détermine comment des noms uniques sont générés pour les membres des hiérarchies contenues dans la dimension de cube. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **Native**:<br />                      [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] détermine automatiquement les noms uniques des membres. Ceci est la valeur par défaut.<br /><br /> **NamePath**: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère un nom composé comprenant le nom de chaque niveau et la légende du membre.|  
|**Nom**|Contient le nom convivial de la dimension de cube. Par défaut, le nom d'une dimension de cube est le même que celui de la dimension de base de données, sauf si une autre dimension de cube du même nom est déjà définie.|  
|**Visible**|Détermine si la dimension de cube est visible. La valeur par défaut est **True**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  

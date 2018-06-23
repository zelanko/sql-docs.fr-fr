---
title: Types de dimension | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1fe0311a992f0f8c067ba6e7096698f96f8bc4bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139688"
---
# <a name="dimension-types"></a>Types de dimensions
  La valeur de la propriété `Type` fournit des informations sur le contenu d'une dimension aux applications serveur et clientes. Dans certains cas, la valeur de `Type` fournit seulement des informations indicatives aux applications clientes et elle est facultative. Dans d'autres cas, comme pour les dimensions `Accounts` ou `Time`, les paramètres de la propriété `Type` pour la dimension et ses attributs déterminent des fonctionnements spécifiques du serveur et peuvent être nécessaires pour implémenter certains fonctionnements du cube. Par exemple, la propriété `Type` d'une dimension peut être définie à la valeur `Accounts` pour indiquer aux applications clientes que la dimension standard contient des attributs de comptes. Pour plus d’informations sur l’heure, le compte et les dimensions de devise, consultez [créer une Dimension de type Date](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [créer un compte Finance de Dimension de type parent-enfant](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), et [créer une devise type de Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 La valeur par défaut pour le type de dimension est `Regular`, qui ne fait pas d'hypothèse quant au contenu de la dimension. Il s'agit de la valeur par défaut pour toutes les dimensions quand vous définissez initialement une dimension, sauf si vous spécifiez `Time` en définissant la dimension avec l'Assistant Dimension. Il est également recommandé de laisser `Regular` comme type de dimension si aucun type approprié de Type de dimension ne figure dans l'Assistant Dimension.  
  
## <a name="available-dimension-types"></a>Types de dimensions disponibles  
 Le tableau suivant décrit les types de dimensions disponibles dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Type de dimension|Description|  
|--------------------|-----------------|  
|Regular|Une dimension dont le type n'a pas été défini avec un type de dimension spécial.|  
|Time|Une dimension dont les attributs représentent des périodes de temps, telles que des années, des semestres, des trimestres, des mois et des jours.|  
|Organization|Une dimension dont les attributs représentent des informations organisationnelles, telles que des employés ou des filiales.|  
|Géographie|Une dimension dont les attributs représentent des informations géographiques, telles que des villes ou des codes postaux.|  
|BillOfMaterials|Une dimension dont les attributs représentent des informations d'inventaire ou de fabrication, telles que des listes de composants pour des produits.|  
|Comptes (Accounts)|Une dimension dont les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.|  
|Customers|Une dimension dont les attributs représentent des informations relatives à des clients ou des contacts.|  
|Products|Une dimension dont les attributs représentent des informations relatives à des produits.|  
|Scénario|Une dimension dont les attributs représentent des informations de planification ou d'analyse stratégique.|  
|Quantitative|Une dimension dont les attributs représentent des informations quantitatives.|  
|Utility|Une dimension dont les attributs représentent des informations diverses.|  
|Monétaire (Currency)|Ce type de dimension contient des données et des métadonnées monétaires.|  
|Rates|Une dimension dont les attributs représentent des informations relatives à des taux de devises.|  
|Channel|Une dimension dont les attributs représentent des informations de canaux.|  
|Promotion|Une dimension dont les attributs représentent des informations de promotion commerciale.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une Dimension à l’aide d’une Table existante](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
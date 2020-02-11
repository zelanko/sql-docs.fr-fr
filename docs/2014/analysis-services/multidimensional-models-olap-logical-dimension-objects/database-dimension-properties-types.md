---
title: Types de dimension | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbe1c8932c082ce537cd5dc3f2b12d98c05c3811
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62728555"
---
# <a name="dimension-types"></a>Types de dimensions
  La valeur de la propriété `Type` fournit des informations sur le contenu d'une dimension aux applications serveur et clientes. Dans certains cas, la valeur de `Type` fournit seulement des informations indicatives aux applications clientes et elle est facultative. Dans d'autres cas, comme pour les dimensions `Accounts` ou `Time`, les paramètres de la propriété `Type` pour la dimension et ses attributs déterminent des fonctionnements spécifiques du serveur et peuvent être nécessaires pour implémenter certains fonctionnements du cube. Par exemple, la propriété `Type` d'une dimension peut être définie à la valeur `Accounts` pour indiquer aux applications clientes que la dimension standard contient des attributs de comptes. Pour plus d’informations sur les dimensions de temps, de compte et de devise, consultez [créer une dimension de type de date](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [créer un compte financier de dimension de type parent-enfant](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)et [créer une dimension de type devise](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 La valeur par défaut pour le type de dimension est `Regular`, qui ne fait pas d'hypothèse quant au contenu de la dimension. Il s'agit de la valeur par défaut pour toutes les dimensions quand vous définissez initialement une dimension, sauf si vous spécifiez `Time` en définissant la dimension avec l'Assistant Dimension. Il est également recommandé de laisser `Regular` comme type de dimension si aucun type approprié de Type de dimension ne figure dans l'Assistant Dimension.  
  
## <a name="available-dimension-types"></a>Types de dimensions disponibles  
 Le tableau suivant décrit les types de dimensions disponibles [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]dans.  
  
|Type de dimension|Description|  
|--------------------|-----------------|  
|Standard |Une dimension dont le type n'a pas été défini avec un type de dimension spécial.|  
|Temps|Une dimension dont les attributs représentent des périodes de temps, telles que des années, des semestres, des trimestres, des mois et des jours.|  
|Organisation|Une dimension dont les attributs représentent des informations organisationnelles, telles que des employés ou des filiales.|  
|Geography|Une dimension dont les attributs représentent des informations géographiques, telles que des villes ou des codes postaux.|  
|BillOfMaterials|Une dimension dont les attributs représentent des informations d'inventaire ou de fabrication, telles que des listes de composants pour des produits.|  
|Comptes|Une dimension dont les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.|  
|Clients|Une dimension dont les attributs représentent des informations relatives à des clients ou des contacts.|  
|Produits|Une dimension dont les attributs représentent des informations relatives à des produits.|  
|Scénario|Une dimension dont les attributs représentent des informations de planification ou d'analyse stratégique.|  
|Quantitative|Une dimension dont les attributs représentent des informations quantitatives.|  
|Utilitaire|Une dimension dont les attributs représentent des informations diverses.|  
|Devise|Ce type de dimension contient des données et des métadonnées monétaires.|  
|Rates|Une dimension dont les attributs représentent des informations relatives à des taux de devises.|  
|Canal|Une dimension dont les attributs représentent des informations de canaux.|  
|Promotion|Une dimension dont les attributs représentent des informations de promotion commerciale.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une dimension à l’aide d’une table existante](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensions &#40;Analysis Services-données multidimensionnelles&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  

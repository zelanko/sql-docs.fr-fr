---
title: Types de dimension | Documents Microsoft
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
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5fa77532b4c674c4b5035cf6b591b973008ae6e5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimension-properties---types"></a>Propriétés de Dimension de base de données - Types
  Le **Type** paramètre de propriété fournit des informations sur le contenu d’une dimension aux applications clientes et serveur. Dans certains cas, le **Type** uniquement fournit des conseils pour les applications clientes et est facultatif. Dans d’autres cas, tel que **comptes** ou **temps** dimensions, les **Type** des paramètres de propriété pour la dimension et ses attributs déterminent des comportements spécifiques basée sur le serveur et peuvent être nécessaires pour implémenter certains comportements dans le cube. Par exemple, le **Type** propriété d’une dimension peut être définie sur **comptes** pour indiquer aux applications clientes que la dimension standard contient des attributs de compte. Pour plus d’informations sur l’heure, le compte et les dimensions de devise, consultez [créer une Dimension de type Date](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [créer un compte Finance de Dimension de type parent-enfant](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), et [créer une Dimension de type devise](../../analysis-services/multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Le paramètre par défaut pour le type de dimension est **régulière**, ce qui ne rend aucune hypothèse quant au contenu de la dimension. Il s’agit du paramètre par défaut pour toutes les dimensions lorsque vous définissez initialement une dimension, sauf si vous spécifiez **temps** lors de la définition de la dimension à l’aide de l’Assistant Dimension. Vous devez également laisser **régulière** comme type de dimension si l’Assistant Dimension ne répertorie pas un type approprié pour le type de Dimension.  
  
## <a name="available-dimension-types"></a>Types de dimensions disponibles  
 Le tableau suivant décrit les types de dimensions disponibles dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Type de dimension| Description|  
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
|Utilitaire|Une dimension dont les attributs représentent des informations diverses.|  
|Monétaire (Currency)|Ce type de dimension contient des données et des métadonnées monétaires.|  
|Rates|Une dimension dont les attributs représentent des informations relatives à des taux de devises.|  
|Channel|Une dimension dont les attributs représentent des informations de canaux.|  
|Promotion|Une dimension dont les attributs représentent des informations de promotion commerciale.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une Dimension à l’aide d’une Table existante](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  


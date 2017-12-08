---
title: "Type d’élément (Dimension) (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (Dimension)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 525259eaaff50d4c5cea5f00a776a1f3b58ab035
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="type-element-dimension-assl"></a>Élément Type (Dimension) (ASSL)
  Fournit des informations sur le contenu de la dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Régulière*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Certaines valeurs de **Type**, par exemple *Accounts*, déterminent un comportement spécifique.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Régulière*|La dimension est une dimension régulière.|  
|*Time*|La dimension est une dimension de temps.<br /><br /> Remarque : Cette valeur indique que la dimension prend en charge les fonctionnalités spécifiques aux dimensions de temps.|  
|*Geography*|La dimension contient des attributs géographiques.|  
|*Organisation*|La dimension contient des attributs d'organisation.|  
|*BillOfMaterials*|La dimension contient des attributs de nomenclature.|  
|*Comptes (Accounts)*|La dimension contient des attributs liés au compte.<br /><br /> Remarque : Cette valeur indique que la dimension prend en charge les fonctionnalités spécifiques aux dimensions de compte.|  
|*Clients*|La dimension contient des attributs liés au client.|  
|*Produits*|La dimension contient des attributs liés au produit.|  
|*Scénario*|La dimension contient des attributs liés au scénario.|  
|*Quantitative*|La dimension contient des attributs quantitatifs.|  
|*Utilitaire*|La dimension contient des attributs d'utilitaire.|  
|*Devise*|La dimension contient des attributs de devise.|  
|*Taux de*|La dimension contient des attributs de taux de change.|  
|*Channel*|La dimension contient des attributs de canal.|  
|*Promotion*|La dimension contient des attributs liés à la promotion.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L’élément qui correspond au parent de **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

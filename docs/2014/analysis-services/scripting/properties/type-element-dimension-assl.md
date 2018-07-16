---
title: Type d’élément (Dimension) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6afa3b273200630a4d36e0c4df679c58efb6bd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283945"
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
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../objects/dimension-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Certaines valeurs pour `Type`, par exemple *comptes*, déterminent un comportement spécifique.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|La dimension est une dimension régulière.|  
|*Time*|La dimension est une dimension de temps. **Remarque :** cette valeur indique que la dimension prend en charge les fonctionnalités spécifiques aux dimensions de temps.|  
|*Geography*|La dimension contient des attributs géographiques.|  
|*Organisation*|La dimension contient des attributs d'organisation.|  
|*BillOfMaterials*|La dimension contient des attributs de nomenclature.|  
|*Comptes (Accounts)*|La dimension contient des attributs liés au compte. **Remarque :** cette valeur indique que la dimension prend en charge les fonctionnalités spécifiques aux dimensions de compte.|  
|*Clients*|La dimension contient des attributs liés au client.|  
|*Produits*|La dimension contient des attributs liés au produit.|  
|*Scénario*|La dimension contient des attributs liés au scénario.|  
|*Quantitatives*|La dimension contient des attributs quantitatifs.|  
|*Utilitaire*|La dimension contient des attributs d'utilitaire.|  
|*Devise*|La dimension contient des attributs de devise.|  
|*Tarifs*|La dimension contient des attributs de taux de change.|  
|*Channel*|La dimension contient des attributs de canal.|  
|*Promotion*|La dimension contient des attributs liés à la promotion.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

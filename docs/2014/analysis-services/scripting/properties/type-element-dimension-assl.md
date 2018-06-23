---
title: Type d’élément (Dimension) (ASSL) | Documents Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 582d5b2052f2681630c5f0cd86facacd5e7cfc91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043690"
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
|*Quantitative*|La dimension contient des attributs quantitatifs.|  
|*Utilitaire*|La dimension contient des attributs d'utilitaire.|  
|*Devise*|La dimension contient des attributs de devise.|  
|*Taux de*|La dimension contient des attributs de taux de change.|  
|*Channel*|La dimension contient des attributs de canal.|  
|*Promotion*|La dimension contient des attributs liés à la promotion.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Type` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
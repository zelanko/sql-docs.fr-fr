---
title: "Slice, élément (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Slice Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Slice
helpviewer_keywords:
- Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ee0b8e31f102cee6e8a73ccd608feec054df6744
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="slice-element-assl"></a>Élément Slice (ASSL)
  Contient une expression MDX (Multidimensional Expressions) qui définit le secteur contenu dans une partition.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **Slice** contient une expression MDX de tuple ou d'ensemble qui identifie la partie du cube pour laquelle la partition stocke des informations. L’expression MDX est semblable à la [StrToSet](../../../mdx/strtoset-mdx.md) fonction MDX avec le mot clé CONSTRAINED, dans la mesure où l’expression ne peut pas inclure de fonctions MDX ou définies par l’utilisateur.  
  
 L’élément qui correspond au parent de **tranche** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

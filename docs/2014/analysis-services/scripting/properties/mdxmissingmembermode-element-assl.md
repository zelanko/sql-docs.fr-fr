---
title: Élément MdxMissingMemberMode (ASSL) | Documents Microsoft
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
- MdxMissingMemberMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MdxMissingMemberMode element
ms.assetid: aca6130b-5fb8-4fa1-af8b-8e1ef361926f
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: feba98157b8e3f6048e0513d7f8b11bb165ca45c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144380"
---
# <a name="mdxmissingmembermode-element-assl"></a>Élément MdxMissingMemberMode (ASSL)
  Détermine comment les membres manquants sont gérés pour les instructions MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension>  
   ...  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Par défaut*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../data-type/dimension-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Ignorer*|Les membres manquants sont ignorés.|  
|*Erreur*|Une erreur est déclenchée si des membres manquants sont détectés.|  
|*Par défaut*|Les membres manquants sont ignorés.|  
  
 L’élément qui correspond au parent de `MdxMissingMemberMode` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions multidimensionnelles &#40;MDX&#41; référence](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

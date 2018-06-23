---
title: Élément SkippedLevelsColumn (ASSL) | Documents Microsoft
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
- SkippedLevelsColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SkippedLevelsColumn
helpviewer_keywords:
- SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3ae469982f39e1274759eaaea992fe456330d8fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043456"
---
# <a name="skippedlevelscolumn-element-assl"></a>Élément SkippedLevelsColumn (ASSL)
    
> [!NOTE]  
>  Cette fonctionnalité n'est plus disponible dans la présente version de Microsoft SQL Server. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.  
  
 Fournit les détails d'une colonne qui stocke le nombre de niveaux omis (vides) entre chaque membre et son parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <SkippedLevelsColumn xsi:type="DataItem">...</SkippedLevelsColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `SkippedLevelsColumn` élément s’applique uniquement aux attributs parents (en d’autres termes, la valeur de la [utilisation](../properties/usage-element-dimensionattribute-assl.md) , élément pour le `DimensionAttribute` parent est défini sur *Parent*). L'élément `SkippedLevelsColumn` contient la colonne ou l'attribut de l'attribut parent qui stocke le nombre de niveaux omis entre chaque membre et son membre parent. Ceci permet aux hiérarchies de type parent-enfant basées sur l'attribut parent d'omettre des niveaux entre des membres. Les valeurs contenues dans cette colonne ou cet attribut doit être des entiers non négatifs ; autrement, une erreur de traitement se produit. Si l'élément `SkippedLevelsColumn` n'est pas spécifié ou ne contient aucune valeur, le membre actuel se trouve à une profondeur inférieure d'un niveau à celle de son membre parent.  
  
 Pour plus d’informations sur la `DataItem` type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la `DataItem` de table, consultez [Type de données DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L’élément qui correspond au parent de `SkippedLevelsColumn` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs d’élément &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Élément de dimension &#40;ASSL&#41;](dimension-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
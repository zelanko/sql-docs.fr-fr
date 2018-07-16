---
title: Élément RootMemberIf (ASSL) | Microsoft Docs
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
- RootMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7ac45d2111b8d3631160ce78f131f98d53230e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280295"
---
# <a name="rootmemberif-element-assl"></a>Élément RootMemberIf (ASSL)
  Détermine la manière dont le membre racine ou les membres d'un attribut parent sont identifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*ParentIsBlankSelfOrMissing*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `RootMemberIf` élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](usage-element-dimensionattribute-assl.md) élément de la `DimensionAttribute` élément parent a la valeur *Parent*) pour déterminer la racine ( membres les plus hauts) d’une hiérarchie parent-enfant.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Seuls les membres qui satisfont à une ou plusieurs des conditions décrites pour *ParentIsBlank*, *ParentIsSelf*, ou *ParentIsMissing* sont traités en tant que membres racines.|  
|*ParentIsBlank*|Seuls les membres avec une valeur null, un zéro ou une chaîne vide dans les colonnes clés représentées par le [KeyColumns](../collections/columns-element-assl.md) collection de `DimensionAttribute` sont traités en tant que membres racines.|  
|*ParentIsSelf*|Seuls les membres qui sont parents d'eux-mêmes sont traités en tant que membres racines.|  
|*ParentIsMissing*|Seuls les membres dont les parents sont introuvables sont traités en tant que membres racines.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `RootMemberIf` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

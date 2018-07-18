---
title: Élément UnknownMemberName (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d744357078e4cfaa73fe3170dba8f1321313efad
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050577"
---
# <a name="unknownmembername-element-assl"></a>Élément UnknownMemberName (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient la légende (dans la langue par défaut de la dimension) du membre inconnu de la dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|*Unknown*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément **UnknownMemberName** fournit la légende utilisée pour le membre inconnu. L'identificateur du membre inconnu est *Dimension*.UnknownMember, où *Dimension* est le nom unique de la dimension et ne peut pas être changé.  
  
 L’élément qui correspond au parent de **UnknownMemberName** dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

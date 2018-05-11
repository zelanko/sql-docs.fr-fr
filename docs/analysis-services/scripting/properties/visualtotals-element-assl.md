---
title: Élément VisualTotals (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8236bdbcf30914da02a96cc72a828b641a5fe51a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="visualtotals-element-assl"></a>Élément VisualTotals (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient une expression MDX (Multidimensional Expressions) qui détermine si les valeurs totales visibles sont affichées pour les membres de cet attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributePermission>  
      ...  
      <VisualTotals>...</VisualTotals>  
   ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|**0**|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **VisualTotals** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

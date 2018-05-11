---
title: Élément IgnoreUnrelatedDimensions (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 42dbcb7a41eec2d620b0a0c098503ff2aa8d2fec
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Élément IgnoreUnrelatedDimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Détermine si les dimensions non liées sont ignorées lorsque des membres de dimensions qui ne sont pas associées au groupe de mesures sont inclus dans une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|True|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Groupe de mesures](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Lorsque **IgnoreUnrelatedDimensions** possède la valeur **true**, les dimensions non liées sont forcées à leur niveau maximum ; lorsque la valeur définie est **false**, les dimensions ne sont pas forcées à leur niveau maximum. Cette propriété est semblable à la MDX (Multidimensional Expressions) [ValidMeasure](../../../mdx/validmeasure-mdx.md) (fonction).  
  
 L’élément qui correspond au parent de **IgnoreUnrelatedDimensions** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

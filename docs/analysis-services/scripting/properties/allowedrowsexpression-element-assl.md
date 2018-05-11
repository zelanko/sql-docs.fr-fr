---
title: Allowedrowsexpression, élément (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7bca46eeaafa4f0e028b08d9f70903f1e6e84b9f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression, élément (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient une expression DAX (Data Analysis), du type booléen, qui définit le contenu de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour le **CellPermission** élément, le **Expression** élément contient une expression MDX logique qui identifie les cellules applicables aux droits indiqués par le [accès](../../../analysis-services/scripting/properties/access-element-assl.md) élément de la **CellPermission** élément. Si la valeur d’un **Expression** , élément pour un **CellPermission** élément est vide, le **CellPermission** élément est ignoré.  
  
 Pour le **StandardAction** élément, le **Expression** élément contient une expression MDX qui représente le contenu de l’action. Si la valeur d’un **Expression** , élément pour un **StandardAction** élément est vide, le **StandardAction** élément est ignoré.  
  
 Les éléments qui correspondent aux parents dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.CellPermission> et <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

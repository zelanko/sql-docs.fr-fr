---
title: Élément QueryDefinition (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d73d50f1c0f31ab8c004fb4644c30a645f96af79
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="querydefinition-element-assl"></a>Élément QueryDefinition (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient une expression opaque pour une requête associée à un [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) élément dans une [QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<QueryBinding>  
   ...  
   <QueryDefinition>...</QueryDefinition>  
   ...  
</QueryBinding>  
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
|Élément parent|[QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **QueryDefinition** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.QueryBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

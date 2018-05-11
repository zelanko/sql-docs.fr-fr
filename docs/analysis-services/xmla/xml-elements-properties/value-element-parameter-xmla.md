---
title: Valeur d’élément (Parameter) (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 904d34b8950246b8ba83b15bb9182d6f04216f30
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="value-element-parameter-xmla"></a>Élément Value (Parameter) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient la valeur d’un paramètre représenté par le [paramètre](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Parameter>  
   ...  
   <Value>...</Value>  
   ...  
</Parameter>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Paramètre](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **valeur** élément peut stocker n’importe quel type XML simple, ainsi que le code XML for Analysis (XMLA) **ensemble de lignes** type de données, pour les paramètres utilisés par les commandes XMLA dans le [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

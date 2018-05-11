---
title: Élément Parameter (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ca615a3ca71d025d95fc56c2d4ec8253b7ce2ba
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="parameter-element-xmla"></a>Élément Parameter (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient le nom et la valeur d'un paramètre utilisé par la méthode [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Paramètres](../../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md)|  
|Éléments enfants|[Nom](../../../analysis-services/xmla/xml-elements-properties/name-element-parameter-xmla.md), [Valeur](../../../analysis-services/xmla/xml-elements-properties/value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Certaines commandes XMLA (XML for Analysis), telles que la commande [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) , peuvent exiger des informations supplémentaires. L'élément **Parameter** offre un mécanisme qui fournit des informations supplémentaires, y compris des informations mémorisées en bloc, à une commande XMLA.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

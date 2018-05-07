---
title: Objet d’élément (Dimension) (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Object Element (Dimension)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: db7feb39-7cc1-4b54-8979-77ce402ef71f
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3f4b942f81b6b4599201f4a15cc61f4993a14258
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="object-element-dimension-xmla"></a>Élément Object (Dimension) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient une référence d’objet pour la dimension sur laquelle le parent [insérer](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [mise à jour](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), ou [supprimer](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) commande est exécutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Insert> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <Database>...</Database>  
      <Cube>...</Cube>  
      <Dimension>...</Dimension>  
   </Object>  
...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [insérer](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [mise à jour](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Éléments enfants|[Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md), [base de données](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md), [Dimension](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

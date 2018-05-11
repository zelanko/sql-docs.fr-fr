---
title: Objet d’élément (Dimension) (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6183485943974072f4532f519021664a2ae7001d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
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
  
  

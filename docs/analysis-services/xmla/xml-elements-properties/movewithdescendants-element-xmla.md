---
title: "Élément MoveWithDescendants (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MoveWithDescendants Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords:
- MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdbacbaa6de4d175d5a1c0223a12a89911ba557a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="movewithdescendants-element-xmla"></a>Élément MoveWithDescendants (XMLA)
  Indique si les descendants des membres d’attribut sont également mis à jour par le parent [mise à jour](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **MoveWithDescendants** élément détermine si le **mettre à jour** commande ne doit pas simplement mettre les membres d’attribut identifiés par le [attributs](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) élément mais également les descendants de ces membres d’attribut sont également mis à jour.  
  
> [!NOTE]  
>  Cet élément s'applique uniquement aux membres d'attribut dans les hiérarchies de type parent-enfant.  
  
 Pour plus d’informations sur la mise à jour des membres, consultez [insertion, mise à jour et suppression de membres &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


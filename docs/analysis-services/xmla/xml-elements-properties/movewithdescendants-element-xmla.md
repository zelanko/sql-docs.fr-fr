---
title: Élément MoveWithDescendants (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a61c8f56ae41d7fd1f58f394ea9adaca4a82ceb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="movewithdescendants-element-xmla"></a>Élément MoveWithDescendants (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
 Pour plus d’informations sur la mise à jour des membres, consultez [insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

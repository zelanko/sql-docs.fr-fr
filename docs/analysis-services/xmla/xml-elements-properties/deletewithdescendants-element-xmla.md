---
title: "Élément DeleteWithDescendants (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DeleteWithDescendants Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d0a75a3cb5de9aba6cd6aeccd90d8342442847c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deletewithdescendants-element-xmla"></a>Élément DeleteWithDescendants (XMLA)
  Indique si les descendants des membres d'attribut sont également supprimés par la commande [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) parente.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
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
|Éléments parents|[DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **DeleteWithDescendants** détermine si la commande **Drop** doit supprimer les membres d'attribut identifiés par l'élément [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md) élément mais également que les descendants de ces membres d'attribut doivent eux aussi être supprimés.  
  
> [!NOTE]  
>  Cet élément s'applique uniquement aux membres d'attribut dans les hiérarchies de type parent-enfant.  
  
 Pour plus d’informations sur la suppression et la mise à jour des membres d’attribut, consultez [Insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

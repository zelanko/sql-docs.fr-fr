---
title: Élément CustomRollup (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CustomRollup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#CustomRollup
- http://schemas.microsoft.com/analysisservices/2003/engine#CustomRollup
- microsoft.xml.analysis.customrollup
helpviewer_keywords:
- CustomRollup element
ms.assetid: b266ac8b-1ae7-461c-9127-3c5642f829f5
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 715aca3e7bb35eb082a9e6fecc286aaf30ff3b71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153107"
---
# <a name="customrollup-element-xmla"></a>Élément CustomRollup (XMLA)
  Contient la formule de cumul personnalisé d’un membre d’attribut représenté par le parent [attribut](attribute-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute>  
   ...  
   <CustomRollup>...</CustomRollup>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribute](attribute-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `CustomRollup` contient une expression MDX (Multidimensional Expressions) qui définit le comportement de cumul du membre d'attribut défini par l'élément `Attribute` parent.  
  
 Pour plus d’informations sur les expressions MDX, consultez [Expressions &#40;MDX&#41;](/sql/mdx/expressions-mdx).  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer l’élément &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

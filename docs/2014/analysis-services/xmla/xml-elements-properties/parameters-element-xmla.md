---
title: Élément Parameters (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Parameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b9c3d0d642ad7248d87e7cc17aaa17953bf6aec
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134049"
---
# <a name="parameters-element-xmla"></a>Élément Parameters (XMLA)
  Contient une collection de [paramètre](parameter-element-xmla.md) éléments utilisés par le [Execute](../xml-elements-methods-execute.md) (méthode).  
  
 **Namespace :** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Exécuter](../xml-elements-methods-execute.md)|  
|Éléments enfants|[Paramètre](parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Certaines commandes XMLA (XML for Analysis), telles que la commande [Process](../xml-elements-commands/process-element-xmla.md) , peuvent exiger des informations supplémentaires. L'élément `Parameters` offre un mécanisme qui fournit des informations supplémentaires, y compris des informations mémorisées en bloc, à une commande XMLA.  
  
 Si la commande XMLA n'utilise pas l'élément `Parameters`, vous pouvez omettre ce dernier lors de l'appel de la méthode `Execute`.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

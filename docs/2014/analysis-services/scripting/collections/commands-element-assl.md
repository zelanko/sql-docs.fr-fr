---
title: Commandes d’élément (ASSL) | Documents Microsoft
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
- Commands Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element
ms.assetid: c9f69fe8-2221-469b-b5b0-08563aaa01dc
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cbbe06ea797473335c5b370e02909cd866205c8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045052"
---
# <a name="commands-element-assl"></a>Élément Commands (ASSL)
  Contient la collection d'éléments [Command](../objects/command-element-assl.md) associée à un élément [MdxScript](../objects/mdxscript-element-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MdxScript>  
   ...  
   <Commands>  
      <Command>...</Command>  
...</Commands>  
   ...  
</MdxScript>  
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
|Élément parent|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Éléments enfants|[Commandee](../objects/command-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CommandCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
---
title: Élément Assemblies (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Assemblies Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Assemblies
helpviewer_keywords:
- Assemblies element
ms.assetid: 8c9be991-0717-4fcf-97d9-13df0f27da05
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ad02db5c06bf45782b22a761dad4f712a223255
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077230"
---
# <a name="assemblies-element-assl"></a>Élément Assemblies (ASSL)
  Contient la collection de [Assembly](../objects/assembly-element-assl.md) éléments associés à un [Server](../objects/server-element-assl.md) ou [base de données](../objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server> <!-- or Database -->  
   ...  
   <Assemblies>  
      <Assembly xsi:type="ClrAssembly">...</Assembly>  
            <Assembly xsi:type="ComAssembly">...</Assembly>  
   </Assemblies>  
   ...  
</Server>  
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
|Éléments parents|[Database](../objects/database-element-assl.md), [Server](../objects/server-element-assl.md)|  
|Éléments enfants|[assembly](../objects/assembly-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AssemblyCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

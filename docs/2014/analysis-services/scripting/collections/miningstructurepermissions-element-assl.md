---
title: Élément MiningStructurePermissions (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructurePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructurePermissions
helpviewer_keywords:
- MiningStructurePermissions element
ms.assetid: 4db9a9b2-8525-441f-a202-fd253282f540
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 191ece4bee99fe3a05ad2452ee58635c69a737b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196089"
---
# <a name="miningstructurepermissions-element-assl"></a>Élément MiningStructurePermissions (ASSL)
  Contient la collection d’autorisations sur un [MiningStructure](../objects/miningstructure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructure>  
   ...  
   <MiningStructurePermissions>  
      <MiningStructurePermission xsi:type="Permission">...</MiningStructurePermission>  
   </MiningStructurePermissions>  
   ...  
</MiningStructure>  
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
|Élément parent|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Éléments enfants|[MiningStructurePermission](../objects/miningstructurepermission-element-assl.md) de type [autorisation](../data-type/permission-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningStructurePermissionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

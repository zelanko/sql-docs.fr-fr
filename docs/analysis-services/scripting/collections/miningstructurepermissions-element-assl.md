---
title: "Élément MiningStructurePermissions (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MiningStructurePermissions Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MiningStructurePermissions
helpviewer_keywords: MiningStructurePermissions element
ms.assetid: 4db9a9b2-8525-441f-a202-fd253282f540
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 04e6b3675bdaa78998fc63479b63ed6db53dca83
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="miningstructurepermissions-element-assl"></a>Élément MiningStructurePermissions (ASSL)
  Contient la collection d’autorisations sur un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) élément.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Éléments enfants|[MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md) de type [autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningStructurePermissionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

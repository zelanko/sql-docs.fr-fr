---
title: "Élément MiningModelPermission (ASSL) | Documents Microsoft"
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
- MiningModelPermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2cd366179355590dca84fb84f8a00e8dfc103a3f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelpermission-element-assl"></a>Élément MiningModelPermission (ASSL)
  Définit les autorisations de membres d’un [rôle](../../../analysis-services/scripting/objects/role-element-assl.md) élément avoir un individu [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|  
|Éléments enfants|[AllowBrowsing](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vous pouvez activer l’extraction sur les structures d’exploration de données en ajoutant le **AllowDrillthrough** autorisé au [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) collection. Si **AllowDrillthrough** est activé sur la structure d’exploration de données et le modèle d’exploration de données, un membre d’un rôle qui a [AllowDrillThrough, élément &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) les autorisations sur le modèle peuvent interroger le modèle d’exploration de données et retourner les colonnes de structure qui n’étaient pas incluses dans le modèle, à l’aide de la syntaxe suivante :  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Par conséquent, pour protéger des données sensibles ou personnelles, vous devez accorder l'autorisation **AllowDrillthrough** sur un modèle d'exploration de données uniquement lorsque cela s'avère nécessaire. Pour plus d’informations, consultez [AllowDrillThrough, élément &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  


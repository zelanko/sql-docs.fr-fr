---
title: Élément MiningModelPermission (ASSL) | Documents Microsoft
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
- MiningModelPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 42a02eedcc2c054269872e4c0f9523ab63632eda
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143792"
---
# <a name="miningmodelpermission-element-assl"></a>Élément MiningModelPermission (ASSL)
  Définit les autorisations de membres d’un [rôle](role-element-assl.md) élément avoir un individu [MiningModel](miningmodel-element-assl.md) élément.  
  
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
|Type de données et longueur|[Autorisation](../data-type/permission-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md)|  
|Éléments enfants|[AllowBrowsing](../properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vous pouvez activer l’extraction sur les structures d’exploration de données en ajoutant le `AllowDrillthrough` autorisé au [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) collection. Si `AllowDrillthrough` est activé sur la structure d’exploration de données et le modèle d’exploration de données, un membre d’un rôle qui a [AllowDrillThrough élément &#40;ASSL&#41; ](../properties/allowdrillthrough-element-assl.md) autorisations sur le modèle peuvent interroger le modèle d’exploration de données et retourner colonnes de structure qui n’étaient pas incluses dans le modèle, à l’aide de la syntaxe suivante :  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Par conséquent, pour protéger des données sensibles ou personnelles, vous devez accorder l'autorisation `AllowDrillthrough` sur un modèle d'exploration de données uniquement lorsque cela s'avère nécessaire. Pour plus d’informations, consultez [AllowDrillThrough élément &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
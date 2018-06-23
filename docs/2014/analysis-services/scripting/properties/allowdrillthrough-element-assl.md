---
title: Élément AllowDrillThrough (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AllowDrillThrough Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: 51
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e5ee132903b98c616ce756b423455302ca6e65f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051148"
---
# <a name="allowdrillthrough-element-assl"></a>Élément AllowDrillThrough (ASSL)
  Détermine si l'extraction est autorisée sur l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|`False`|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Élément MiningModel](../objects/miningmodel-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `AllowDrillThrough` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission> et <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Extraction sur des structures d'exploration de données  
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vous pouvez définir `AllowDrillthrough` autorisations pour les structures d’exploration de données, ainsi que les modèles d’exploration de données. Lorsque vous assignez cette autorisation à un rôle, tout membre de ce rôle peut interroger le modèle d'exploration de données et retourner les colonnes de la structure qui n'étaient pas incluses dans le modèle. Par exemple, vous créez un modèle qui utilise uniquement les colonnes : clé du client, revenus du client et achats du client. Si vous activez l'extraction sur le modèle, les utilisateurs peuvent retourner des informations dans d'autres colonnes de la structure d'exploration de données, telles que les adresses de messagerie ou les noms des clients.  
  
 Par conséquent, pour protéger les données sensibles, soyez prudent lorsque vous ajoutez des colonnes à la structure d'exploration de données. Également, accordez l'autorisation `AllowDrillthrough` sur une structure seulement lorsqu'elle est requise.  
  
 Pour procéder à l'extraction des colonnes de la structure, utilisez une requête avec l'une des syntaxes suivantes :  
  
 `SELECT * FROM <structure>.CASES`  
  
 ou Gestionnaire de configuration  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
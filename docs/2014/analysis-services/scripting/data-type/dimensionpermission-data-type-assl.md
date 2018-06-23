---
title: Type de données DimensionPermission (ASSL) | Documents Microsoft
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
- DimensionPermission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DimensionPermission data type
ms.assetid: 066405ff-903f-467a-b0d5-e58653952c52
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1c614d2fd30f7bd3b831c571cc4d3de0cf26e365
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050910"
---
# <a name="dimensionpermission-data-type-assl"></a>Type de données DimensionPermission (ASSL)
  Définit un type de données dérivé représentant les autorisations attribuées à une dimension de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionPermission>  
   <!-- The following elements extend Permission -->  
   <AttributePermissions>...</AttributePermissions>  
   <AllowedRowsExpression>...</AllowedRowsExpression>  
</DimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Autorisation](permission-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[AttributePermissions](../collections/attributepermissions-element-assl.md), [AllowedRowsExpression](../collections/attributepermissions-element-assl.md)|  
|Éléments dérivés|[DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément a les validations suivantes sous la valeur 2 de DeploymentMode (mode de serveur tabulaire).  
  
-   L'attribut*AttributePermission* doit être vide ou une erreur se produit.  
  
 Cet élément a les validations suivantes sous la valeur 0 de DeploymentMode (OLAP).  
  
-   L'attribut*AllowedRowsExpression* doit être vide ou une erreur se produit.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DimensionPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
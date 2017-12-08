---
title: "Type de données DimensionPermission (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: DimensionPermission Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DimensionPermission data type
ms.assetid: 066405ff-903f-467a-b0d5-e58653952c52
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d0cafbd3a0c86682d3993a5e32547d0430b751a1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Types de données de base|[Autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md), [AllowedRowsExpression](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|  
|Éléments dérivés|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément a les validations suivantes sous la valeur 2 de DeploymentMode (mode de serveur tabulaire).  
  
-   L'attribut*AttributePermission* doit être vide ou une erreur se produit.  
  
 Cet élément a les validations suivantes sous la valeur 0 de DeploymentMode (OLAP).  
  
-   L'attribut*AllowedRowsExpression* doit être vide ou une erreur se produit.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DimensionPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

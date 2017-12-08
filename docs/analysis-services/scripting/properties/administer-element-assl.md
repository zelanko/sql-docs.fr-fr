---
title: "Élément Administer (ASSL) | Documents Microsoft"
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
apiname: Administer Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Administer
helpviewer_keywords: Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: de42ea2bc2782f03aa31b875f8a6a6c3758dcb12
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="administer-element-assl"></a>Élément Administer (ASSL)
  Indique si l’autorisation associée inclut le droit d’administrer un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **Administer** indique si un utilisateur peut exercer des fonctions d'administration uniquement sur la base de données spécifiée. Le rôle d'administrateur de serveur peut exercer des fonctions administratives sur toutes les bases de données que contient l'instance.  
  
 L’élément qui correspond au parent de **administrer** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Élément role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

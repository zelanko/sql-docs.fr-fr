---
title: "Élément KeyErrorLimitAction (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: KeyErrorLimitAction Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyErrorLimitAction
helpviewer_keywords: KeyErrorLimitAction element
ms.assetid: a2a01aae-0571-499f-9025-b61c741f3ddb
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a41842fe6ffbf2df18b9ecf4ef234f78d16f887b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="keyerrorlimitaction-element-assl"></a>Élément KeyErrorLimitAction (ASSL)
  Spécifie l’action [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend lorsque le nombre d’erreurs de la clé est spécifié dans le [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md) est atteint.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*StopProcessing*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*StopProcessing*|Arrête le traitement de l'objet.|  
|*StopLogging*|Poursuit le traitement de l'objet mais cesse l'enregistrement des erreurs survenues au cours de ce traitement.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **KeyErrorLimitAction** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.KeyErrorLimitAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

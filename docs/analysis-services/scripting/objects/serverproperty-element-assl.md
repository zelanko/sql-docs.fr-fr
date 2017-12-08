---
title: "Élément ServerProperty (ASSL) | Documents Microsoft"
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
apiname: ServerProperty Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SERVERPROPERTY
helpviewer_keywords: ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edf7c78a2486d7e09dfb8eeb437b1215bff50bc1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="serverproperty-element-assl"></a>Élément ServerProperty (ASSL)
  Définit une propriété de serveur associée à un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|  
|Éléments enfants|[DefaultValue](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md), [DisplayFlag](../../../analysis-services/scripting/properties/displayflag-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [PendingValue](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md), [RequiresRestart](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md), [valeur](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Le **ServerProperty** élément décrit les données et les métadonnées pour une propriété de serveur associée à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Contrairement aux éléments figurant dans d'autres collections dans ASSL (Analysis Services Scripting Language), l'élément **ServerProperty** utilise des paires nom/valeur à la place d'éléments portant des noms explicites pour décrire les propriétés de serveur. Les paires nom/valeur garantissent souplesse et extensibilité.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Server, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

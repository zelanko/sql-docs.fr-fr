---
title: "Élément DesignAggregations (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DesignAggregations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords:
- DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0a20166ec005068195d93ee22c40837213944445
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="designaggregations-element-xmla"></a>Élément DesignAggregations (XMLA)
  Crée des agrégations pour une conception d’agrégation sur une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
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
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Matérialiser](../../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md), [objet](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [optimisation](../../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md), [requêtes](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md), [étapes](../../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md), [stockage](../../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md), [heure](../../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande **DesignAggregations** est utilisée pour générer des définitions d'agrégation stockées par une conception d'agrégation. Une conception d'agrégation peut être utilisée ensuite pour matérialiser des agrégations pour une partition et peut être réutilisée entre des partitions.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  


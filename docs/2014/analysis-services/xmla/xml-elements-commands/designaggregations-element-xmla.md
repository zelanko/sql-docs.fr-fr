---
title: Élément DesignAggregations (XMLA) | Documents Microsoft
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
- DesignAggregations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords:
- DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d448a7cc815dddcc4e9568831f2d652fc7a22680
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153562"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Matérialiser](../xml-elements-properties/materialize-element-xmla.md), [objet](../xml-elements-properties/object-element-xmla.md), [optimisation](../xml-elements-properties/optimization-element-xmla.md), [requêtes](../xml-elements-properties/queries-element-xmla.md), [étapes](../xml-elements-properties/steps-element-xmla.md), [stockage](../xml-elements-properties/storage-element-xmla.md) , [Heure](../xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `DesignAggregations` est utilisée pour générer des définitions d'agrégation stockées par une conception d'agrégation. Une conception d'agrégation peut être utilisée ensuite pour matérialiser des agrégations pour une partition et peut être réutilisée entre des partitions.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
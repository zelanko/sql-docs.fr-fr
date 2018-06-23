---
title: Élément Binding (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Binding Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.binding
- http://schemas.microsoft.com/analysisservices/2003/engine#Binding
- urn:schemas-microsoft-com:xml-analysis#Binding
helpviewer_keywords:
- Binding element
ms.assetid: d5acd8d4-8551-449a-ae30-d0ba828cc02d
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fe6f67a91ac410596601ffd2d5e440a0de727d0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141410"
---
# <a name="binding-element-xmla"></a>Élément Binding (XMLA)
  Définit une liaison hors ligne pour une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] un objet, tel qu’un attribut dans une dimension, pour le [liaisons](bindings-element-xmla.md) collection d’un [lot](../xml-elements-commands/batch-element-xmla.md) ou [ Processus](../xml-elements-commands/process-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Bindings>  
   <Binding xsi:type="DimensionAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="MeasureGroupAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="PartitionBinding">...</Binding>  
</Bindings>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DimensionAttributeBinding](../../scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md), [MeasureGroupAttributeBinding](../../scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [PartitionBinding](../../scripting/data-type/binding-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Liaisons](bindings-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments `Binding` définissent des liaisons hors ligne, autres que les sources de données et les vues de source de données, pour les objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] que doit traiter une commande `Batch` ou `Process`. Pour plus d’informations sur le traitement des objets, consultez [le traitement des objets &#40;XMLA&#41;](../xml-elements-objects.md).  
  
 Pour plus d’informations sur les liaisons hors ligne, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
---
title: "Élément Synchronize (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Synchronize Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords: Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e3361f8cdd01421561bbb6b16d4b6cf5675a356
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="synchronize-element-xmla"></a>Élément Synchronize (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Synchronise un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données avec une autre base de données existante.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
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
|Éléments parents|[Commandee](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [emplacements](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Notes   
 Le **synchroniser** commande synchronise la base de données cible avec une instance de la source et la base de données spécifiée dans le **Source** élément. Si vous le souhaitez, le **synchroniser** commande synchronise les partitions distantes définies dans la base de données source.  
  
 Selon le mode de stockage utilisé par les objets stockés dans le fichier de sauvegarde, le **synchroniser** commande synchronise les informations répertoriées dans le tableau suivant.  
  
|Mode de stockage|Informations|  
|------------------|-----------------|  
|OLAP multidimensionnel (MOLAP)|Données sources, agrégations et métadonnées|  
|Hybrid OLAP (HOLAP)|Agrégations et métadonnées|  
|OLAP relationnel (ROLAP)|Métadonnées|  
  
 Pendant un **synchroniser** de commande, un verrou de lecture est placé sur la base de données source et un verrou d’écriture est placé sur la base de données cible. Les deux verrous sont libérés après le **synchroniser** commande est terminée.  
  
 Pour plus d’informations sur la synchronisation des bases de données, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Backup &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Élément de lot &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Élément Parallel &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Restaurer l’élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

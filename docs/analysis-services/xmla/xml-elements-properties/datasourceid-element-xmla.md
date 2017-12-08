---
title: "L’élément DataSourceID (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourceID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.datasourceid
- urn:schemas-microsoft-com:xml-analysis#DataSourceID
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceID
helpviewer_keywords: DataSourceID element
ms.assetid: 695522c7-acca-420a-a5fb-f01f3fd9a96b
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fc7845f5cbd36d3e8696a7ad24ed834975de87e8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="datasourceid-element-xmla"></a>Élément DataSourceID (XMLA)
  Identifie une source de données utilisée par un [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) élément pendant une [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location>  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **DataSourceID** élément contient le nom de la source de données sur l’instance source qui identifie l’instance distante sur laquelle les informations de partition distante doit être sauvegardée, restaurée ou synchronisés.  
  
 Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ConnectionString &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Élément DataSourceType &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

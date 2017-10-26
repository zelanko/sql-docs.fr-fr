---
title: "Élément ReadWriteMode | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3075b7834f7e24004811ce3802dd5fcb55b56f6c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="readwritemode-element"></a>Élément ReadWriteMode
  La propriété de base de données **ReadWriteMode** spécifie si la base de données est en mode **ReadWrite** ou en mode **ReadOnly** . Ce sont les deux seules valeurs possibles de la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|ReadWrite|  
|Cardinalité|0-1 : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Base de données](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les bases de données sont créées uniquement en mode **ReadWrite** . Les bases de données ne peuvent pas être créées en mode **ReadOnly** .  
  
 La valeur de l'élément **ReadWriteMode** est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*En lecture seule*|Aucune modification ou mise à jour ne peut être appliquée à la base de données.|  
|*Lecture/écriture*|Les modifications et mises à jour peuvent être appliquées à la base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Attach](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Attacher et détacher des bases de données Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  


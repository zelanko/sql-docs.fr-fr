---
title: Élément ReadWriteMode | Microsoft Docs
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
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3577feacc65bc1d7259d95af9b5bc6179e72b3b9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285785"
---
# <a name="readwritemode-element"></a>Élément ReadWriteMode
  La propriété de base de données `ReadWriteMode` spécifie si la base de données est en mode `ReadWrite` ou en mode `ReadOnly`. Ce sont les deux seules valeurs possibles de la propriété.  
  
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
|Éléments parents|[Base de données](database-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les bases de données sont créées uniquement en mode `ReadWrite`. Les bases de données ne peuvent pas être créées en mode `ReadOnly`.  
  
 La valeur de l'élément `ReadWriteMode` est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*En lecture seule*|Aucune modification ou mise à jour ne peut être appliquée à la base de données.|  
|*Lecture/écriture*|Les modifications et mises à jour peuvent être appliquées à la base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Attach](../xml-elements-commands/attach-element.md)   
 [Attacher et détacher des bases de données Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](../../multidimensional-models/database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  

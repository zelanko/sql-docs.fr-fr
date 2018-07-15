---
title: Élément DataSourceType (XMLA) | Microsoft Docs
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
- DataSourceType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords:
- DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c911f2a0e224cb8ccc9e7fa5b32a89a972fd1c26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207669"
---
# <a name="datasourcetype-element-xmla"></a>Élément DataSourceType (XMLA)
  Indique si un [emplacement](location-element-xmla.md) élément spécifié pour un [restaurer](../xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../xml-elements-commands/synchronize-element-xmla.md) commande est local ou distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*À distance*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](location-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `DataSourceType` détermine si la source de données définie par l'élément `Location` contient une source de données locale ou une source de données distante. Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Local*|L'élément `Location` définit une source de données locale. Si vous utilisez cette valeur, les commandes `Restore` et `Synchronize` exploitent les informations définies dans l'élément `Location` (informations extraites à partir du fichier de sauvegarde spécifié dans l'élément `File` de la commande `Backup` ou depuis la base de données spécifiée dans l'élément `Source` de la commande `Synchronize`) dans le but de mettre à jour la source de données identifiée dans l'élément `DataSourceID` de l'élément `Location`.<br /><br /> Cette valeur autorise les objets qui adoptent le stockage OLAP relationnel (ROLAP) relationnel (après avoir été restaurés ou synchronisés) afin d'utiliser une base de données différente pour leurs données et leurs métadonnées. **Remarque :** données ROLAP, telles que les données dans les tables de dimension ou les tables d’écriture différée ne sont pas restaurées ou synchronisées. Seules les métadonnées des objets ROLAP le sont.|  
|*À distance*|L'élément `Location` définit une source de données distante. Si vous utilisez cette valeur, les commandes `Restore` et `Synchronize` exploitent les informations définies dans l'élément `Location` (informations récupérées à partir du fichier de sauvegarde spécifié dans l'élément `File` de la commande `Backup` ou depuis la base de données spécifiée dans l'élément `Source` de la commande `Synchronize`) dans le but de restaurer ou de synchroniser les partitions distantes sur l'instance distante identifiée dans l'élément `DataSourceID` de l'élément `Location`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ConnectionString &#40;XMLA&#41;](connectionstring-element-xmla.md)   
 [Élément DataSourceID &#40;XMLA&#41;](id-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

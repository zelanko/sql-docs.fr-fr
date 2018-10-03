---
title: Élément location (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Location Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0277ab50eb7390d3272c309df8dc865ff088c89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107610"
---
# <a name="location-element-xmla"></a>Élément Location (XMLA)
  Contient des informations sur un serveur distant pour le parent [sauvegarde](../xml-elements-commands/backup-element-xmla.md), [restaurer](../xml-elements-commands/restore-element-xmla.md), ou [synchroniser](../xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Location>  
```  
  
```  
  
<File>...</File> <!-- for Backup and Restore only -->  
<DataSourceID>...</DataSourceID>  
<DataSourceType>...</DataSourceType> <!-- for Restore and Synchronize only -->  
<ConnectionString>...</ConnectionString> <!-- for Restore and Synchronize only -->  
<Folders>...</Folders> <!-- for Restore and Synchronize only -->  
```  
  
```  
  
   </Location>  
   ...  
</Backup>  
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
|Éléments parents|[Sauvegarde](../xml-elements-commands/backup-element-xmla.md), [restaurer](../xml-elements-commands/restore-element-xmla.md), [synchroniser](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Ancêtre ou parent|Élément enfant|  
|------------------------|-------------------|  
|[Sauvegarde](id-element-xmla.md), [fichier](file-element-xmla.md)|  
|[Restaurer](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [fichier](file-element-xmla.md), [dossiers](folders-element-xmla.md)|  
|[Synchroniser](../xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [dossiers](folders-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Pour `Backup` commandes, le `Location` élément fournit des informations sur la création d’un fichier de sauvegarde à distance pour une instance distante de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Pour les commandes `Restore`, l'élément `Location` fournit des informations sur l'identification et la connexion à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] distante, ainsi que sur le fichier de sauvegarde distant utilisé pour restaurer des partitions distantes sur cette même instance distante.  
  
 Pour les commandes `Synchronize`, l'élément `Location` décrit une source de données que doit utiliser l'instance cible ou une instance distante définie sur l'instance source qui doit être synchronisée avec l'instance cible, selon la valeur de l'élément `DataSourceType` pour la commande `Synchronize` parente.  
  
 Pour plus d’informations sur la sauvegarde et restauration des instances distantes, consultez [sauvegarde et restauration des objets (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BackupRemotePartitions &#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

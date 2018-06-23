---
title: Élément location (XMLA) | Documents Microsoft
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
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 51b0838b9843658b4081f9464c63274631ed74be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152419"
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
  
  
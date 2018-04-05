---
title: Élément location (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Location Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a08e989924a4cd8a3f32c32debeb8560470e7684
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="location-element-xmla"></a>Élément Location (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contient des informations sur un serveur distant pour le parent [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
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
|Éléments parents|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Éléments enfants|Consultez le tableau ci-dessous.|  
  
|Ancêtre ou parent|Élément enfant|  
|------------------------|-------------------|  
|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [fichier](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[Restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [fichier](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [dossiers](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[Synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [dossiers](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>Notes   
 Pour **sauvegarde** commandes, le **emplacement** élément fournit des informations sur la création d’un fichier de sauvegarde à distance pour une instance distante de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Pour **restaurer** commandes, le **emplacement** élément fournit des informations sur l’identification et la connexion à une distance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, ainsi que le fichier de sauvegarde distant utilisé pour restaurer les partitions distantes sur cette instance distante.  
  
 Pour les commandes **Synchronize** , l'élément **Location** décrit une source de données que doit utiliser l'instance cible ou une instance distante définie sur l'instance source qui doit être synchronisée avec l'instance cible, selon la valeur de l'élément **DataSourceType** pour la commande **Synchronize** parente.  
  
 Pour plus d’informations sur la sauvegarde et restauration des instances distantes, consultez [sauvegarde et restauration des objets (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BackupRemotePartitions &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

---
title: Fichier d’élément (XMLA) | Microsoft Docs
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
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b75a261f4a86d5a227e1018ad96a40d91db7b6c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319219"
---
# <a name="file-element-xmla"></a>Élément File (XMLA)
  Identifie un fichier à utiliser par le parent [sauvegarde](../xml-elements-commands/backup-element-xmla.md) ou [restaurer](../xml-elements-commands/restore-element-xmla.md) commande, ou par le parent [emplacement](location-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../xml-elements-commands/backup-element-xmla.md), [emplacement](location-element-xmla.md), [restaurer](../xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `File` contient un nom de fichier UNC, et l'élément parent détermine l'utilisation de l'élément `File`.  
  
 Pour les commandes `Backup`, l'élément `File` détermine le nom du fichier de sauvegarde créé par la commande `Backup`. Si un chemin d’accès n’est pas spécifié en tant que partie du nom de fichier, le chemin d’accès spécifié dans le `BackupDir` propriété de configuration pour l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est utilisé. Si le fichier spécifié existe déjà, une erreur se produit, sauf si l'élément `AllowOverwrite` de la commande `Backup` parente possède la valeur `True`.  
  
 Pour les commandes `Restore`, l'élément `File` détermine le nom du fichier de sauvegarde à restaurer par la commande `Restore`.  
  
 Pour les éléments `Location`, l'élément `File` décrit un fichier de sauvegarde distant pour une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui contient des partitions distantes. Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AllowOverwrite &#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

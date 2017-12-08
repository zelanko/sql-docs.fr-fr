---
title: "Fichier de l’élément (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords: File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d098aa61edb8d51b7a3868b21b768b7ab286e48c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="file-element-xmla"></a>Élément File (XMLA)
  Identifie un fichier à utiliser par le parent [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) ou [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) commande, ou par le parent [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) élément.  
  
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **fichier** élément contient un nom de fichier UNC et que l’élément parent détermine l’utilisation de la **fichier** élément.  
  
 Pour **sauvegarde** commandes, le **fichier** élément détermine le nom du fichier de sauvegarde créé par le **sauvegarde** commande. Si un chemin d’accès n’est pas spécifié en tant que partie du nom de fichier, le chemin d’accès spécifié dans le **BackupDir** propriété de configuration pour l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est utilisé. Si le fichier spécifié existe déjà, une erreur se produit, sauf si le **AllowOverwrite** élément du parent **sauvegarde** commande est définie sur **True**.  
  
 Pour **restaurer** commandes, le **fichier** élément détermine le nom du fichier de sauvegarde à restaurer par le **restaurer** commande.  
  
 Pour **emplacement** éléments, le **fichier** élément décrit un fichier de sauvegarde à distance pour un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance qui contient des partitions distantes. Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AllowOverwrite &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

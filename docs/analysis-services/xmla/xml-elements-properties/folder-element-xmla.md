---
title: "Élément Folder (XMLA) | Documents Microsoft"
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
apiname:
- Folder Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.folder
- http://schemas.microsoft.com/analysisservices/2003/engine#Folder
- urn:schemas-microsoft-com:xml-analysis#Folder
helpviewer_keywords:
- Folder element
ms.assetid: 87b305b0-57e3-4ec3-9d80-f1bcf3ce7540
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4e3a685de817e213923c6eba8f4cb251fe574a5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="folder-element-xmla"></a>Élément Folder (XMLA)
  Contient un emplacement de stockage de système de fichiers mettre à jour pour un [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) élément pendant une [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Dossiers](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Éléments enfants|[Nouvelle](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [d’origine](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 S'il est spécifié, l'élément **Folder** modifie les emplacements de stockage des objets contenus dans le fichier de sauvegarde (pour les commandes **Restore** ) ou dans la base de données de l'instance source (pour les commandes **Synchronize** ) permettant de faire correspondre la valeur de l'élément **Original** avec celle de l'élément **New** .  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément StorageLocation &#40; ASSL &#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


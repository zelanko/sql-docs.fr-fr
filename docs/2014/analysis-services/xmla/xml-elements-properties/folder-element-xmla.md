---
title: Élément Folder (XMLA) | Documents Microsoft
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
- Folder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folder
- http://schemas.microsoft.com/analysisservices/2003/engine#Folder
- urn:schemas-microsoft-com:xml-analysis#Folder
helpviewer_keywords:
- Folder element
ms.assetid: 87b305b0-57e3-4ec3-9d80-f1bcf3ce7540
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64bc73db4cfb1fee4471e474bf498094751edcf5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050900"
---
# <a name="folder-element-xmla"></a>Élément Folder (XMLA)
  Contient un emplacement de stockage de système de fichiers mettre à jour pour un [emplacement](location-element-xmla.md) élément pendant une [restaurer](../xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../xml-elements-commands/synchronize-element-xmla.md) commande.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Dossiers](folders-element-xmla.md)|  
|Éléments enfants|[Nouvelle](new-element-xmla.md), [d’origine](original-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 S'il est spécifié, l'élément `Folder` modifie les emplacements de stockage des objets contenus dans le fichier de sauvegarde (pour les commandes `Restore`) ou dans la base de données de l'instance source (pour les commandes `Synchronize`) permettant de faire correspondre la valeur de l'élément `Original` avec celle de l'élément `New`.  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément StorageLocation &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
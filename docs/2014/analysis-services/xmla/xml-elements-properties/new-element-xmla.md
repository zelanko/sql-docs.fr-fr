---
title: Nouvel élément (XMLA) | Documents Microsoft
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
- New Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#New
- microsoft.xml.analysis.new
- urn:schemas-microsoft-com:xml-analysis#New
helpviewer_keywords:
- New element
ms.assetid: 1321adcb-67f7-40f0-8f20-b17c1d3e3f17
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 983c32cc19ebbc876d53d46865f81b0d37e10d59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140364"
---
# <a name="new-element-xmla"></a>Élément New (XMLA)
  Contient le nouvel emplacement de stockage de système fichier utilisé par un [dossier](folder-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
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
|Éléments parents|[Dossier](folder-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `New` contient un chemin UNC qui remplace la valeur de l'élément `Original` que contient l'élément `Folder` parent pour tous les objets restaurés ou synchronisés pendant une commande `Restore` ou `Synchronize`. La valeur de l'élément `Original` est comparée à la valeur de l'élément `StorageLocation` pour chaque cube, groupe de mesures ou partition et, si une correspondance est trouvée, la valeur de cet élément est utilisée pour mettre à jour l'élément `StorageLocation` de l'objet pendant la restauration ou la synchronisation.  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde et restauration des objets (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément d’origine &#40;XMLA&#41;](original-element-xmla.md)   
 [Élément Restore &#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Élément StorageLocation &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Élément Synchronize &#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
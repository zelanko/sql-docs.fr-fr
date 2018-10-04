---
title: Élément d’origine (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Original Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b09f2388c47206b1b879a5c8dc98f10a28675342
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212069"
---
# <a name="original-element-xmla"></a>Élément Original (XMLA)
  Contient l’emplacement de stockage d’origine du système de fichiers utilisé par un [dossier](folder-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
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
 Le `Original` élément contient un chemin d’accès UNC à remplacer par la valeur de la [New](new-element-xmla.md) élément contenu dans le parent `Folder` élément pour tous les objets restaurés ou synchronisés, respectivement, pendant un [restaurer ](../xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../xml-elements-commands/synchronize-element-xmla.md) commande. La valeur de cet élément est comparée à la valeur de la [StorageLocation](../../scripting/properties/storagelocation-element-assl.md) élément pour chaque groupe de mesures, la partition ou le cube et, si une correspondance est trouvée, la valeur de la `New` élément est utilisé pour mettre à jour le `StorageLocation` de la objet au cours de restauration ou la synchronisation.  
  
 Pour plus d’informations sur la sauvegarde et restauration d’objets, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

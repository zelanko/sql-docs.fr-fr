---
title: Type d’élément (XMLA) | Documents Microsoft
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
- Type Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 38b4442afe95f06d9a6f437e906c01b7386d91ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050898"
---
# <a name="type-element-xmla"></a>Élément Type XMLA
  Détermine le type de traitement à effectuer par le [processus](../xml-elements-commands/process-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traiter](../xml-elements-commands/process-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les options de traitement disponibles pour les objets sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consultez [traitement d’un objet de modèle multidimensionnel](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 La valeur de l'élément `Type` est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*ProcessFull*|Supprime toutes les données de l'objet affecté, puis traite l'objet affecté.|  
|*ProcessAdd*|Ajoute de nouvelles données à l'objet affecté.|  
|*ProcessUpdate*|Actualise les données de l'objet affecté.|  
|*ProcessIndexes*|Crée ou reconstruit des index et des agrégations dans l'objet affecté.|  
|*ProcessScriptCache*|Si le cube est traité, le serveur reconstruit le cache des scripts MDX. Sinon, une erreur est générée.<br /><br /> **Remarque** s’applique uniquement au cube.|  
|*ProcessData*|Traite uniquement les données de l'objet affecté.|  
|*ProcessDefault*|Détecte l'état de l'objet affecté puis effectue l'option de traitement appropriée sur l'objet affecté afin de l'optimiser pleinement et de le remettre dans un état complètement traité.|  
|*ProcessClear*|Supprime les données dans l'objet affecté et tous les objets connexes.|  
|*ProcessStructure*|Traite uniquement la structure de l'objet affecté.|  
|*ProcessClearStructureOnly*|Efface uniquement les données de l'objet affecté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
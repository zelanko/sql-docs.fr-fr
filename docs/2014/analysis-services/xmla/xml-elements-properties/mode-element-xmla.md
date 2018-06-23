---
title: Élément mode (XMLA) | Documents Microsoft
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
- Mode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5634e273e1708f9de213436e20008cc6874f50a7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155120"
---
# <a name="mode-element-xmla"></a>Élément Mode (XMLA)
  Identifie le mode à utiliser par le parent [verrou](../xml-elements-commands/lock-element-xmla.md) élément lors de la création d’un verrou sur un objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
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
|Éléments parents|[Verrou](../xml-elements-commands/lock-element-xmla.md), [déverrouiller](../xml-elements-commands/unlock-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `Lock` parent utilise l'élément `Mode` pour déterminer le type de verrou à créer sur un objet. La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*CommitShared*|Un verrou partagé est établi sur l'objet spécifié. D'autres verrous partagés peuvent être créés pour le même objet.<br /><br /> Un verrou partagé empêche les transactions contenant des opérations d’écriture, telles qu’une [Execute](../xml-elements-methods-execute.md) appel de méthode en cours d’exécution un [Alter](../xml-elements-commands/alter-element-xmla.md) commande sur un objet spécifié, à partir de la validation jusqu'à ce que le verrou partagé est supprimé. Un verrou partagé n’empêche pas les transactions contenant des opérations de lecture, comme un [Discover](../xml-elements-methods-discover.md) appel de méthode ou un `Execute` appel de méthode en cours d’exécution un [instruction](../xml-elements-commands/statement-element-xmla.md) commande à partir de la validation.|  
|*CommitExclusive*|Un verrou exclusif est établi sur l'objet spécifié. Aucun autre verrou partagé ou exclusif ne peut être créé pour le même objet.<br /><br /> Jusqu'à sa suppression, un verrou exclusif empêche la validation des transactions contenant des opérations de lecture ou d'écriture sur un objet spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ID &#40;XMLA&#41;](id-element-xmla.md)   
 [Élément objet &#40;XMLA&#41;](object-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
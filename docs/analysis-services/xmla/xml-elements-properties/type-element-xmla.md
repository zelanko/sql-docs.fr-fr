---
title: Type d’élément (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a080a1af46df731befc8ab66ce925b961be9b16
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34576711"
---
# <a name="type-element-xmla"></a>Élément Type XMLA
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Détermine le type de traitement à effectuer par le [processus](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l’élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traiter](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les options de traitement disponibles pour les objets sur une instance d’Analysis Services, consultez [du traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 La valeur de la **Type** élément est limitée à une des chaînes répertoriées dans le tableau suivant.  
  
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
 [Propriétés &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

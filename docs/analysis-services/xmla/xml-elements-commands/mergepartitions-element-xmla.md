---
title: Élément MergePartitions (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4cfe28f42c56e73109b3d3d939f433e48b09ed43
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="mergepartitions-element-xmla"></a>Élément MergePartitions (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Fusionne les données d'une ou plusieurs partitions sources dans une partition cible, puis supprime les partitions sources.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <MergePartitions>  
      <Sources>...</Sources>  
      <Target>...</Target>  
   </MergePartitions>  
</Command>  
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
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Sources](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md), [Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Toutes les références à des objets dans les éléments **Sources** et **Target** doivent pointer sur des partitions distinctes dans le même groupe de mesures. Sinon, une erreur se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

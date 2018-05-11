---
title: Élément SkippedLevels (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 091b86cd6465e6a55cefe6b52ed2ed4488ea9cc5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="skippedlevels-element-xmla"></a>Élément SkippedLevels (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient le nombre de niveaux ignorés par un membre d'attribut représenté par l'élément [Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute>  
   ...  
   <SkippedLevels>...</SkippedLevels>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|0|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **SkippedLevels** détermine le nombre de niveaux ignorés par un membre d'attribut défini par l'élément **Attribute** parent.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer un élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Mettre à jour, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

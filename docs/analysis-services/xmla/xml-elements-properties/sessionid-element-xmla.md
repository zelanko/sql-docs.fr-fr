---
title: Élément SessionID (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bb853b0aefcc5a32acde0ca0c07711127ece38e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="sessionid-element-xmla"></a>Élément SessionID (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifie une session active sur laquelle exécuter l'élément [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cancel>  
   ...  
   <SessionID>...</SessionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Annuler](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CancelAssociated & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Élément ConnectionID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Élément SPID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

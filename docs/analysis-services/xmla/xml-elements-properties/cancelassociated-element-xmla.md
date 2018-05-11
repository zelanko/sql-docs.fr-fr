---
title: Élément CancelAssociated (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 97d8d3fbc5980d9e6ffab788af5c9a3cf61fcc15
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="cancelassociated-element-xmla"></a>Élément CancelAssociated (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique si l'élément [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) parent doit annuler toutes les commandes associées.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Annuler](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si cet élément est spécifié et possède la valeur **True**, toutes les connexions, sessions et commandes correspondantes identifiées dans la commande **Cancel** parente sont annulées.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ConnectionID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Élément SessionID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Élément SPID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

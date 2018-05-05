---
title: Élément SessionID (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SessionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#SessionID
- http://schemas.microsoft.com/analysisservices/2003/engine#SessionID
- microsoft.xml.analysis.sessionid
helpviewer_keywords:
- SessionID element
ms.assetid: 18220e00-76cf-48f6-9465-200465a0c553
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e5769b2337e59bef05167d11ac1ff18578770639
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
  

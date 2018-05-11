---
title: Élément SPID (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2c665e40334710a631d10e236b26360a87277de
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="spid-element-xmla"></a>Élément SPID (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifie un identificateur de processus (SPID) de serveur actif sur lequel exécuter le parent [Annuler](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cancel>  
   ...  
   <SPID>...</SPID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Annuler](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **SPID** élément représente le processus serveur ID (SPID) utilisé pour une session donnée sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CancelAssociated & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Élément ConnectionID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Élément SessionID & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

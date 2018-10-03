---
title: Élément SPID (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SPID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#SPID
- microsoft.xml.analysis.spid
- urn:schemas-microsoft-com:xml-analysis#SPID
helpviewer_keywords:
- SPID element
ms.assetid: c4a54dcb-a0cd-4255-9e0f-a34eb990854f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 47a220caccafa9288a8fa9176b52db05297ff477
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094522"
---
# <a name="spid-element-xmla"></a>Élément SPID (XMLA)
  Identifie un identificateur de processus (SPID) de serveur actif sur lequel exécuter le parent [Annuler](../xml-elements-commands/cancel-element-xmla.md) élément.  
  
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
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Annuler](../xml-elements-commands/cancel-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `SPID` élément représente le processus serveur ID (SPID) utilisé pour une session donnée sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CancelAssociated &#40;XMLA&#41;](cancelassociated-element-xmla.md)   
 [Élément ConnectionID &#40;XMLA&#41;](id-element-xmla.md)   
 [Élément SessionID &#40;XMLA&#41;](sessionid-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

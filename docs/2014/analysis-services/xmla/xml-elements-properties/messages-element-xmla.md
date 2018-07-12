---
title: Messages, élément (XMLA) | Microsoft Docs
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
- Messages Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0fbaba30716831ef34a40dd94c6c9b2ab507641
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176776"
---
# <a name="messages-element-xmla"></a>Élément Messages (XMLA)
  Contient une collection de [Message](message-element-xmla.md) éléments retournés à partir d’une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] par un [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) (méthode) appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Jeu de résultats](../xml-data-types/resultset-data-type-xmla.md)|  
|Éléments enfants|[Boîte de](message-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément est utilisé dans les cas où l'exécution d'un appel de méthode `Discover` ou d'une seule commande XMLA contenue dans un appel de méthode `Execute` réussit mais s'accompagne d'erreurs ou d'avertissements. Dans ce cas, un `Messages` élément est ajouté à la [racine](root-element-xmla.md) élément après tous les autres éléments, qui à son tour contient un ou plusieurs `Message` éléments. Chaque `Message` élément représente un seul message, une erreur ou un avertissement, retourné par la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

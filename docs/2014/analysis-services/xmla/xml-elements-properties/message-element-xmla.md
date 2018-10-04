---
title: Message, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Message Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.message
- http://schemas.microsoft.com/analysisservices/2003/engine#Message
- urn:schemas-microsoft-com:xml-analysis#Message
helpviewer_keywords:
- Message element
ms.assetid: 028911e2-9779-43b1-824d-6d7fb2295885
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4aebaf918701d4ce10cfda9a4f3c030b53404e9f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054062"
---
# <a name="message-element-xmla"></a>Élément Message (XMLA)
  Contient un message retourné d'une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] par un appel de méthode [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Messages>  
   ...  
   <Message>  
      <Error>...</Error>  
      <!-- or -->  
      <Warning>...</Warning>  
   </Message>  
   ...  
</Messages>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Messages](messages-element-xmla.md)|  
|Éléments enfants|[Erreur](error-element-xmla.md), [Avertissement](warning-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément est utilisé dans les cas où l'exécution d'un appel de méthode `Discover` ou d'une seule commande XMLA contenue dans un appel de méthode `Execute` réussit mais s'accompagne d'erreurs ou d'avertissements. En pareil cas, un élément `Messages` contenant lui-même un ou plusieurs éléments `Message` est ajouté à l'élément racine après tous les autres éléments. Chaque `Message` élément représente un seul message, une erreur ou un avertissement, retourné par la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

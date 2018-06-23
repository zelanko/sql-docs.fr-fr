---
title: Élément CommitTransaction (XMLA) | Documents Microsoft
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
- CommitTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CommitTransaction
- urn:schemas-microsoft-com:xml-analysis#CommitTransaction
- microsoft.xml.analysis.committransaction
helpviewer_keywords:
- CommitTransaction command
ms.assetid: 1cd814dc-a0be-4305-b44d-faf15e843f7d
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 85db6f53386023acb32a9e853ad1d69f92f6860c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041884"
---
# <a name="committransaction-element-xmla"></a>Élément CommitTransaction (XMLA)
  Valide une transaction sur la session active avec un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <CommitTransaction />  
</Command>  
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
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La commande `CommitTransaction` valide une transaction active, définie explicitement à l'aide de l'élément `BeginTransaction`, sur la session active. S'il n'existe pas encore de transaction active, une erreur se produit. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] décrémente le nombre de référence de transactions pour la session active. Si le nombre de référence de transactions actives définies explicitement atteint zéro, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] valide la transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BeginTransaction &#40;XMLA&#41;](begintransaction-element-xmla.md)   
 [Élément Cancel &#40;XMLA&#41;](cancel-element-xmla.md)   
 [Élément RollbackTransaction &#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
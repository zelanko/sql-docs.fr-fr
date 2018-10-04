---
title: Élément RollbackTransaction (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RollbackTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords:
- RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ae78f589c1c85713c751a737d6fb93fac9efeda
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218810"
---
# <a name="rollbacktransaction-element-xmla"></a>Élément RollbackTransaction (XMLA)
  Restaure une transaction sur la session active avec une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
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
 La commande `RollbackTransaction` restaure toutes les transactions actives, définies explicitement à l'aide de l'élément `BeginTransaction`, sur la session active. S'il n'existe pas encore de transaction active, une erreur se produit. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] décrémente à zéro le nombre de référence de transactions pour la session active et restaure toutes les transactions actives.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BeginTransaction &#40;XMLA&#41;](begintransaction-element-xmla.md)   
 [Élément Cancel &#40;XMLA&#41;](cancel-element-xmla.md)   
 [Élément CommitTransaction &#40;XMLA&#41;](committransaction-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  

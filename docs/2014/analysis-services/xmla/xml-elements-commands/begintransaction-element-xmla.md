---
title: Élément BeginTransaction (XMLA) | Documents Microsoft
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
- BeginTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e85979e1e791dcd3c2bb5b19ef5c615f73975e07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051590"
---
# <a name="begintransaction-element-xmla"></a>Élément BeginTransaction (XMLA)
  Commence une transaction sur la session active avec une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <BeginTransaction />  
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
 La commande `BeginTransaction` démarre une transaction active dans la session active. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrémente le nombre de référence de transactions pour la session active. Dans le cas inverse, l'instance entame une nouvelle transaction et définit le décompte de références de la session active à 1. Si une transaction active est définie de manière explicite par le biais de la commande `BeginTransaction`, toutes les commandes suivantes sont exécutées à l'intérieur de la transaction explicitement définie.  
  
 Lorsque la session active arrive à son terme et que le nombre de référence de transactions est supérieur à zéro, toutes les transactions actives sont restaurées.  
  
 Si aucune transaction active n'est explicitement définie sur la session active, toutes les commandes émises sur cette session sont exécutées à l'intérieur d'une transaction implicitement définie. La transaction implicite est validée si la commande réussit ou est restaurée en cas d'échec de la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Cancel &#40;XMLA&#41;](cancel-element-xmla.md)   
 [Élément CommitTransaction &#40;XMLA&#41;](committransaction-element-xmla.md)   
 [Élément RollbackTransaction &#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
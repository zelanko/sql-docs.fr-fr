---
title: "Élément CommitTransaction (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CommitTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CommitTransaction
- urn:schemas-microsoft-com:xml-analysis#CommitTransaction
- microsoft.xml.analysis.committransaction
helpviewer_keywords:
- CommitTransaction command
ms.assetid: 1cd814dc-a0be-4305-b44d-faf15e843f7d
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94e3d90ec0e59226045fc12e460768abbb6ae78a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La commande **CommitTransaction** valide une transaction active, définie explicitement à l'aide de l'élément **BeginTransaction** , sur la session active. S'il n'existe pas encore de transaction active, une erreur se produit. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] décrémente le nombre de référence de transactions pour la session active. Si le nombre de référence de transactions actives définies explicitement atteint zéro, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] valide la transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BeginTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Annuler, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Élément RollbackTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  


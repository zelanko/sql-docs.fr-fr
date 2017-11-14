---
title: "Élément BeginTransaction (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BeginTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 677ad07e9ce6206bbc4e7946ec111f8865bcfcce
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La commande **BeginTransaction** démarre une transaction active dans la session active. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrémente le nombre de référence de transactions pour la session active. Dans le cas inverse, l'instance entame une nouvelle transaction et définit le décompte de références de la session active à 1. Si une transaction active est définie de manière explicite par le biais de la commande **BeginTransaction** , toutes les commandes suivantes sont exécutées à l'intérieur de la transaction explicitement définie.  
  
 Lorsque la session active arrive à son terme et que le nombre de référence de transactions est supérieur à zéro, toutes les transactions actives sont restaurées.  
  
 Si aucune transaction active n'est explicitement définie sur la session active, toutes les commandes émises sur cette session sont exécutées à l'intérieur d'une transaction implicitement définie. La transaction implicite est validée si la commande réussit ou est restaurée en cas d'échec de la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Annuler, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Élément CommitTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Élément RollbackTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  


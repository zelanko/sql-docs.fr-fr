---
title: "Élément RollbackTransaction (XMLA) | Documents Microsoft"
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
apiname: RollbackTransaction Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords: RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7c4e44239047729e0989f8a2b8d5dbca9487c967
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La commande **RollbackTransaction** restaure toutes les transactions actives, définies explicitement à l'aide de l'élément **BeginTransaction** , sur la session active. S'il n'existe pas encore de transaction active, une erreur se produit. Si une transaction active existe déjà, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] décrémente à zéro le nombre de référence de transactions pour la session active et restaure toutes les transactions actives.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BeginTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Annuler, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Élément CommitTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

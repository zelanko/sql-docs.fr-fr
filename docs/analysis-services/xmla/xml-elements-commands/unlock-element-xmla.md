---
title: Élément Unlock (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Unlock Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Unlock
- urn:schemas-microsoft-com:xml-analysis#Unlock
- microsoft.xml.analysis.unlock
helpviewer_keywords:
- Unlock command
ms.assetid: 46425b33-baa2-41ad-803a-34d2fb4b2cab
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e898471957c96ea35b1214cd389eb6ba8ebc901d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="unlock-element-xmla"></a>Élément Unlock (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Déverrouille un verrou spécifié sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Unlock>  
      <ID>...</ID>  
   </Unlock>  
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
|Éléments parents|[Commandee](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)|  
  
## <a name="remarks"></a>Notes   
 La commande **Unlock** supprime un verrou établi dans le contexte de la transaction actuellement active. Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Unlock** de manière explicite.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Verrouiller l’élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

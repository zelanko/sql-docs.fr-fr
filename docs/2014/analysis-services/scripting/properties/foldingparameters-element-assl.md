---
title: Élément FoldingParameters (ASSL) | Microsoft Docs
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
topic_type:
- apiref
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac348aa326c53b1266edfff3396feadda6c80ea6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161140"
---
# <a name="foldingparameters-element-assl"></a>Élément FoldingParameters (ASSL)
  Spécifie les paramètres utilisés par le serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] lorsqu'il effectue une validation croisée de modèles d'exploration de données.  
  
> [!NOTE]  
>  Ces paramètres sont réservés à un usage interne uniquement. Les présentes informations sont fournies à titre de référence uniquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|*FoldIndex*|Entier qui indique la position de départ de la partition qui est utilisée pour la validation croisée.|  
|*FoldCount*|Entier qui indique le nombre de partitions dans le modèle après la validation croisée.|  
|*MaxCases*|Entier qui indique le nombre de cas de modèles utilisés pour la validation croisée.<br /><br /> Une valeur 0 indique que tous les cas sont utilisés.|  
|*FoldTargetAttribute*|Chaîne qui indique l'ID de la colonne du modèle qui contient l'attribut prédictible.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Éléments enfants|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Notes  
 Ces propriétés sont réservées à un usage interne uniquement, et ne sont pas prises en charge pour une utilisation dans les instructions DDL.  
  
 Pour plus d’informations sur l’utilisation de la validation croisée dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], consultez [mesures dans le rapport de Validation croisée](../../data-mining/measures-in-the-cross-validation-report.md).  
  
 Pour plus d’informations sur la façon d’effectuer la validation croisée à l’aide de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] des procédures stockées, consultez [procédures stockées d’exploration de données &#40;Analysis Services - Exploration de données&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

---
title: "Élément FoldingParameters (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: Schema
applies_to:
- SQL Server 2016 Preview
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
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ddfadd34b6d0b0ae7ba459f35ccb7c1fa7faa31a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
  
|Caractéristique| Description|  
|--------------------|-----------------|  
|*FoldIndex*|Entier qui indique la position de départ de la partition qui est utilisée pour la validation croisée.|  
|*FoldCount*|Entier qui indique le nombre de partitions dans le modèle après la validation croisée.|  
|*MaxCases*|Entier qui indique le nombre de cas de modèles utilisés pour la validation croisée.<br /><br /> Une valeur 0 indique que tous les cas sont utilisés.|  
|*FoldTargetAttribute*|Chaîne qui indique l'ID de la colonne du modèle qui contient l'attribut prédictible.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Éléments enfants|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Notes  
 Ces propriétés sont réservées à un usage interne uniquement, et ne sont pas prises en charge pour une utilisation dans les instructions DDL.  
  
 Pour plus d’informations sur l’utilisation de la validation croisée dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], consultez [mesures dans le rapport de Validation croisée](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Pour plus d’informations sur la façon d’effectuer la validation croisée à l’aide de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] des procédures stockées, consultez [les procédures stockées d’exploration de données &#40; Analysis Services - Exploration de données &#41; ](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


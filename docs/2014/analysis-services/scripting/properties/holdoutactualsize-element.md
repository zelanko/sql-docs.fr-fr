---
title: Élément HoldoutActualSize | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f74b11b9032285bf45bc8b7705953adf6d58f04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297279"
---
# <a name="holdoutactualsize-element"></a>Élément HoldoutActualSize
  Indique la taille réelle, après traitement, de la partition d’exclusion qui contient le jeu de tests d’un [MiningStructure](../objects/miningstructure-element-assl.md) élément. Les cas restants dans le jeu de données sont utilisés pour l'apprentissage. Cette propriété est en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Valeur entière en lecture seule.|  
|Valeur par défaut|Non applicable|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de `HoldoutActualSize` dépend de la source de données et sur les valeurs de [HoldoutMaxCases](holdoutmaxcases-element.md), [HoldoutMaxPercent](holdoutmaxpercent-element.md), et [HoldoutSeed](holdoutseed-element.md). Par conséquent, la valeur de `HoldoutActualSize` n'est pas disponible tant que [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] n'a pas fini de traiter la structure d'exploration de données.  
  
 L’élément qui correspond au parent de `HoldoutActualSize` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prenait pas en charge l'utilisation de partitions d'exclusion sur une structure d'exploration de données. Par conséquent, les instructions ASSL ([!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language) qui contiennent un des paramètres d'exclusion `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` ou `HoldoutActualSize` ne peuvent pas être utilisées dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous utilisez l'un de ces paramètres d'exclusion dans une instruction ASSL dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)   
 [Holdoutmaxcases, élément](holdoutmaxcases-element.md)   
 [Holdoutmaxpercent, élément](holdoutmaxpercent-element.md)   
 [HoldoutSeed, élément](holdoutseed-element.md)  
  
  

---
title: "HoldoutActualSize (élément) | Documents Microsoft"
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
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 24a26b453f90fc82e91b1572b0e79af6477caa22
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="holdoutactualsize-element"></a>Élément HoldoutActualSize
  Indique la taille réelle, après traitement, de la partition d’exclusion qui contient le jeu de tests d’un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) élément. Les cas restants dans le jeu de données sont utilisés pour l'apprentissage. Cette propriété est en lecture seule.  
  
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
|Élément parent|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de **HoldoutActualSize** dépend de la source de données et sur les valeurs de [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md), [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md), et [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md). Par conséquent, la valeur de **HoldoutActualSize** n’est pas disponible tant que [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] traite la structure d’exploration de données.  
  
 L’élément qui correspond au parent de **HoldoutActualSize** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prenait pas en charge l'utilisation de partitions d'exclusion sur une structure d'exploration de données. Par conséquent, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] les instructions de langage de script (ASSL) qui contiennent l’un des paramètres d’exclusion, **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, ou **HoldoutActualSize**, ne peut pas être utilisé dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous utilisez l'un de ces paramètres d'exclusion dans une instruction ASSL dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Holdoutmaxcases, élément](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Holdoutmaxpercent, élément](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Holdoutseed, élément](../../../analysis-services/scripting/properties/holdoutseed-element.md)  
  
  


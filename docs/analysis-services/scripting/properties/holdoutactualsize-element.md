---
title: HoldoutActualSize (élément) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d4d761f3964cd133d8576597f69004c0555f522f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="holdoutactualsize-element"></a>Élément HoldoutActualSize
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Propriétés &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Holdoutmaxcases, élément](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Holdoutmaxpercent, élément](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [HoldoutSeed, élément](../../../analysis-services/scripting/properties/holdoutseed-element.md)  
  
  

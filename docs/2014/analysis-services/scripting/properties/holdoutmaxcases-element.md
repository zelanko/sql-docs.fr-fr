---
title: Élément HoldoutMaxCases | Documents Microsoft
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
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 083ff97f8d739f4f970a6fec8a5c7353b43b5763
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152432"
---
# <a name="holdoutmaxcases-element"></a>Élément HoldoutMaxCases
  Spécifie le nombre maximal de cas dans la source de données à utiliser pour la partition d’exclusion qui contient le jeu de tests d’un [MiningStructure](../objects/miningstructure-element-assl.md) élément. Les cas restants dans le jeu de données sont utilisés pour l'apprentissage. Une valeur de 0 indique qu'il n'existe aucune limite au nombre des cas pouvant être exclus en tant que jeu de tests.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier supérieur à 0.|  
|Valeur par défaut|0|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si vous spécifiez des valeurs pour `HoldoutMaxPercent` et `HoldoutMaxCases`, l'algorithme limite le jeu de tests à la plus petite des deux valeurs.  
  
 Si `HoldoutMaxCases` a la valeur par défaut de 0 et si aucune valeur n'est affectée à `HoldoutMaxPercent`, l'algorithme utilise le jeu de données entier pour l'apprentissage.  
  
 Les nouvelles propriétés `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, ou `HoldoutActualSize` sont uniquement disponibles dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et versions ultérieures. Par conséquent, vous devez préfixer ces propriétés avec le nouvel espace de noms comme indiqué dans la description de la syntaxe sans quoi [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prenait pas en charge l'utilisation de partitions d'exclusion sur une structure d'exploration de données. Par conséquent, les instructions ASSL ([!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language) qui contiennent un des paramètres d'exclusion `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` ou `HoldoutActualSize` ne peuvent pas être utilisées dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous utilisez l'un de ces paramètres d'exclusion dans une instruction ASSL dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
 L’élément qui correspond au parent de `HoldoutMaxCases` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)   
 [Holdoutmaxpercent, élément](holdoutmaxpercent-element.md)   
 [Holdoutseed, élément](holdoutseed-element.md)   
 [HoldoutActualSize, élément](holdoutactualsize-element.md)  
  
  
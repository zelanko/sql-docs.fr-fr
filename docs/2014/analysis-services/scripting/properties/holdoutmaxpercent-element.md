---
title: Holdoutmaxpercent, élément | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ef3a056404f350ea8b9bfe5d369b9091bad0de9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140269"
---
# <a name="holdoutmaxpercent-element"></a>Élément HoldoutMaxPercent
  Spécifie le pourcentage maximal de cas dans la source de données qui sera utilisée pour la partition d’exclusion qui contient le jeu de tests d’un [MiningStructure](../objects/miningstructure-element-assl.md) élément. Les cas restants sont utilisés pour l'apprentissage. Une valeur de 0 indique qu'il n'existe aucune limite au nombre des cas pouvant être exclus en tant que jeu de tests.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier compris entre 0 et 99.|  
|Valeur par défaut|30|  
|Cardinalité|0-1 : Élément facultatif qui peut se produire une seule fois seulement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si vous spécifiez des valeurs pour `HoldoutMaxPercent` et `HoldoutMaxCases`, l'algorithme limite le jeu de tests à la plus petite des deux valeurs.  
  
 Si `HoldoutMaxCases` a la valeur par défaut de 0 et si aucune valeur n'est affectée à `HoldoutMaxPercent`, l'algorithme utilise le jeu de données complet pour l'apprentissage.  
  
 Les nouvelles propriétés `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, ou `HoldoutActualSize` sont uniquement disponibles dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et versions ultérieures. Par conséquent, vous devez préfixer ces propriétés en utilisant le nouvel espace de noms comme indiqué dans la description de la syntaxe sans quoi [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prenait pas en charge l'utilisation de partitions d'exclusion sur une structure d'exploration de données. Par conséquent, les instructions ASSL ([!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language) qui contiennent un des paramètres d'exclusion `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` ou `HoldoutActualSize` ne peuvent pas être utilisées dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous utilisez l'un de ces paramètres d'exclusion dans une instruction ASSL dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
 L’élément qui correspond au parent de `HoldoutMaxPercent` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)   
 [Holdoutmaxcases, élément](holdoutmaxcases-element.md)   
 [Holdoutseed, élément](holdoutseed-element.md)   
 [HoldoutActualSize, élément](holdoutactualsize-element.md)  
  
  

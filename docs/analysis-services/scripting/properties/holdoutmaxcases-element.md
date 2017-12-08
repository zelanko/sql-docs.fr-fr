---
title: "Élément HoldoutMaxCases | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: HoldoutMaxCases
helpviewer_keywords: HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 96558785d84797018b6a0ba4cf0d0b370127443e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="holdoutmaxcases-element"></a>Élément HoldoutMaxCases
  Spécifie le nombre maximal de cas dans la source de données à utiliser pour la partition d’exclusion qui contient le jeu de tests d’un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) élément. Les cas restants dans le jeu de données sont utilisés pour l'apprentissage. Une valeur de 0 indique qu'il n'existe aucune limite au nombre des cas pouvant être exclus en tant que jeu de tests.  
  
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
|Élément parent|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si vous spécifiez des valeurs pour les deux **HoldoutMaxPercent** et **HoldoutMaxCases**, l’algorithme limite la jeu de tests à la plus petite des deux valeurs.  
  
 Si **HoldoutMaxCases** a la valeur par défaut de 0, et une valeur n’a pas été définie pour **HoldoutMaxPercent**, l’algorithme utilise l’ensemble de données pour l’apprentissage.  
  
 Les nouvelles propriétés **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, ou **HoldoutActualSize** sont uniquement disponibles dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et versions ultérieures. Par conséquent, vous devez préfixer ces propriétés avec le nouvel espace de noms comme indiqué dans la description de la syntaxe sans quoi [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne prenait pas en charge l'utilisation de partitions d'exclusion sur une structure d'exploration de données. Par conséquent, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] les instructions de langage de script (ASSL) qui contiennent l’un des paramètres d’exclusion, **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, ou **HoldoutActualSize**, ne peut pas être utilisé dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous utilisez l'un de ces paramètres d'exclusion dans une instruction ASSL dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
 L’élément qui correspond au parent de **HoldoutMaxCases** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Holdoutmaxpercent, élément](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Holdoutseed, élément](../../../analysis-services/scripting/properties/holdoutseed-element.md)   
 [HoldoutActualSize, élément](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)  
  
  

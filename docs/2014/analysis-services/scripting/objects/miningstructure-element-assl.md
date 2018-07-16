---
title: Élément MiningStructure (ASSL) | Microsoft Docs
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
api_name:
- MiningStructure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed39aafbe937c637abd7a6ec67fbd7343b62b116
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271825"
---
# <a name="miningstructure-element-assl"></a>Élément MiningStructure (ASSL)
  Définit la structure d'un ensemble de modèles d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
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
|Éléments parents|[MiningStructures](../collections/miningstructures-element-assl.md)|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CacheMode](../properties/cachemode-element-assl.md), [classement](../properties/collation-element-assl.md), [colonnes](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Description ](../properties/description-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../properties/holdoutseed-element.md),<br /><br /> [ID](../properties/id-element-assl.md), [langage](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModels](../collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md), [nom](../properties/name-element-assl.md), [Source](../properties/source-element-binding-assl.md), [état](../properties/state-element-assl.md), [traductions](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La structure d'exploration de données définit les colonnes et les liaisons. Après avoir défini une structure d'exploration de données, vous pouvez utiliser cette structure pour définir de nombreux modèles d'exploration de données. La structure d'exploration de données, et chaque modèle d'exploration de données qu'elle contient, peuvent être traités indépendamment.  
  
> [!NOTE]  
>  Les propriétés d'exclusion, `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` et `HoldoutActualSize` ont été introduites dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Elles vous permettent de définir une partition sur une structure d'exploration de données qui joue le rôle de jeu de test pour tous les modèles d'exploration de données associés à la structure. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ne prend pas en charge ces propriétés. Par conséquent, si vous essayez d'utiliser ces propriétés sur une instance de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne une erreur.  
  
## <a name="drillthrough-to-structure-columns"></a>Extraction dans des colonnes de structure  
 Dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], un nouvel élément d’autorisation a été ajouté à la [MiningStructurePermissions élément &#40;ASSL&#41; ](../collections/miningstructurepermissions-element-assl.md) collection. Si vous ajoutez `AllowDrillthrough` autorisation à la fois à la [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) et [MiningModelPermission](miningmodelpermission-element-assl.md) collections, d’extraction est activée à partir du modèle d’exploration de données à la structure, de manière que les membres d’un rôle ayant `AllowDrillthrough` autorisations sur le modèle peuvent interroger le modèle d’exploration de données et retourner des colonnes de structure qui n’étaient pas incluses dans le modèle.  
  
 Par conséquent, pour protéger les données sensibles ou personnelles, vous devez construire votre vue de source de données pour masquer les informations sensibles et accorder `AllowDrillthrough` autorisation sur une structure d’exploration de données uniquement lorsque cela est nécessaire. Pour plus d’informations, consultez [AllowDrillThrough élément &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)   
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](/sql/dmx/select-dmx)  
  
  

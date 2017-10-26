---
title: "L’élément NullProcessing (ASSL) | Documents Microsoft"
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NullProcessing Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc5c99e52f8868251d7d5b581bdefcea6e5d3097
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
  Définit le mode de traitement des valeurs NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Automatic*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Conserver*|Conserve la valeur NULL.<br /><br /> Remarque : Cette valeur n’est pas prise en charge pour les mesures de comptage.|  
|*Erreur*|Déclenche une erreur de clé NULL. La valeur de [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md) détermine comment l’instance réagit à l’erreur.<br /><br /> Remarque : Cette valeur n’est pas prise en charge pour les mesures.|  
|*UnknownMember*|Génère un membre inconnu et déclenche une erreur de conversion de valeur NULL. La valeur de [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md) détermine comment l’instance réagit à l’erreur.<br /><br /> Remarque : Cette valeur n’est pas prise en charge pour les colonnes associées aux mesures.|  
|*ZeroOrBlank*|Convertit la valeur NULL en zéro (pour les éléments de données numériques) ou en une chaîne vide (pour les éléments de données de type chaîne).<br /><br /> Remarque : Cette valeur assure la compatibilité avec les versions précédentes de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatic*|Utilise le traitement par défaut approprié pour l'élément :<br /><br /> *ZeroOrBlank* pour les éléments de données OLAP.<br /><br /> *UnknownMember* pour les éléments de données d'exploration de données.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **NullProcessing** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


---
title: "Élément NullKeyConvertedToUnknown (ASSL) | Documents Microsoft"
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
apiname:
- NullKeyConvertedToUnknown Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77c93a56563f621d357943348cf436846f213068
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Élément NullKeyConvertedToUnknown (ASSL)
  Spécifie l'action à entreprendre en cas d'erreur de conversion de type NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*IgnoreError*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les erreurs de conversion de valeur NULL se produisent lorsqu'une valeur NULL est rencontrée dans une colonne clé et interprétée comme membre **Unknown** . Toutefois, cette erreur se produit uniquement si le [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) , élément pour les [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) ancêtre de la **ErrorConfiguration** élément parent a la valeur *UnknownMember*.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IgnoreError*|Le traitement ignore l'erreur et continue.|  
|*ReportAndContinue*|Le traitement signale l'erreur et continue.|  
|*ReportAndStop*|Le traitement signale l'erreur et s'arrête.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **NullKeyConvertedToUnknown** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

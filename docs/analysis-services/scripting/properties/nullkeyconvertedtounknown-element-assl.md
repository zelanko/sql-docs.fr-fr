---
title: Élément NullKeyConvertedToUnknown (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c3d101e2577a7e691aae685bcf821979b5640182
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Élément NullKeyConvertedToUnknown (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Élément ErrorConfiguration & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

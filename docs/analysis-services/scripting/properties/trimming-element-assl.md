---
title: Élément Trimming (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 34b985292408fa253d65bbdecf1630f12ab2eb9b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="trimming-element-assl"></a>Élément Trimming (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie comment les données de la source de données sont tronquées.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   ...  
   <Trimming>...</Trimming>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Oui*|  
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
|*Gauche*|Les données sont tronquées à gauche.|  
|*Oui*|Les données sont tronquées à droite.|  
|*LeftRight*|Les données sont tronquées à gauche et à droite.|  
|*Aucun*|Les données ne sont pas tronquées.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **Trimming** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Trimming>.  
  
 L’élément qui correspond au parent de **Trimming** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

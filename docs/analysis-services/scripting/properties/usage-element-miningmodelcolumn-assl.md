---
title: Élément usage (MiningModelColumn) (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a7e3326deb1ea9c67b3b64daa5f01efef817c4de
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Élément Usage (MiningModelColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Décrit comment la colonne associée dans le parent [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) est utilisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Clé*|La colonne est une colonne clé.|  
|*Entrée*|La colonne est une colonne d'entrée.|  
|*Predict*|La colonne est une colonne de prévision.|  
|*PredictOnly*|La colonne est uniquement une colonne de prévision.|  
|*Aucun*|La colonne n'est pas utilisée par le modèle.<br /><br /> **\*\* Avertissement \* \***  lorsque la valeur de l’utilisation est « None », Analysis Services n’envoie pas n’importe quelle valeur au serveur par défaut ; par conséquent, l’attribut d’utilisation n’est pas inclus dans la demande/réponse.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **utilisation** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

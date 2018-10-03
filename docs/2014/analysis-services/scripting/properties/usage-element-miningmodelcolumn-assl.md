---
title: Élément usage (MiningModelColumn) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 220f59e5e342f61f30d0f94bc9f9728982105986
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090296"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Élément Usage (MiningModelColumn) (ASSL)
  Décrit comment la colonne associée de la page parente [MiningStructure](../objects/miningstructure-element-assl.md) est utilisé.  
  
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
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Clé*|La colonne est une colonne clé.|  
|*entrée*|La colonne est une colonne d'entrée.|  
|*Predict*|La colonne est une colonne de prévision.|  
|*PredictOnly*|La colonne est uniquement une colonne de prévision.|  
|*Aucun*|La colonne n'est pas utilisée par le modèle. **Avertissement :** lorsque la valeur de l’utilisation est « None », Analysis Services n’envoie pas n’importe quelle valeur au serveur par défaut ; par conséquent, l’attribut de l’utilisation n’est pas inclus dans la demande/réponse.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Usage` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

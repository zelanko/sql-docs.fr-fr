---
title: Type d’élément (Action) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af38eb6a60e8e54ecfc4ac5bb4fb05faeab69feb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168419"
---
# <a name="type-element-action-assl"></a>Élément Type (Action) (ASSL)
  Contient le type de la [Action](../objects/action-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../objects/action-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*URL*|Affiche une page qui varie selon le cas dans un navigateur Internet.|  
|*HTML*|Exécute un script HTML dans un navigateur Internet.|  
|*Instruction*|Exécute une commande OLE DB.|  
|*Extraction*|Récupère un ensemble de lignes pour l'extraction.<br /><br /> Cette valeur est identique à *ensemble de lignes* et identifie les actions d’extraction. Il peut uniquement être utilisé sur les actions dont la propriété [TargetType](targettype-element-assl.md) a la valeur *cellules*.|  
|*Jeu de données*|Récupère un dataset.|  
|*Rowset*|Récupère un ensemble de lignes.|  
|*ligne de commande*|Exécute une commande à une invite de commandes.|  
|*Propriétaire*|Effectue une opération en utilisant une interface différente de celles répertoriées plus haut dans ce tableau.|  
|*Rapport*|Affiche une page qui varie selon le cas dans un navigateur Internet.<br /><br /> Cette valeur est identique à *Url* et identifie des actions de rapport.|  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données DrillThroughAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Type de données ReportAction &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

---
title: "Type d’élément (Action) (ASSL) | Documents Microsoft"
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
apiname: Type Element (Action)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3a84623ef5ee2b870e767217ae5f8664ac44d517
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="type-element-action-assl"></a>Élément Type (Action) (ASSL)
  Contient le type de la [Action](../../../analysis-services/scripting/objects/action-element-assl.md) élément.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*URL*|Affiche une page qui varie selon le cas dans un navigateur Internet.|  
|*HTML*|Exécute un script HTML dans un navigateur Internet.|  
|*Instruction*|Exécute une commande OLE DB.|  
|*Extraction*|Récupère un ensemble de lignes pour l'extraction.<br /><br /> Cette valeur est identique à *ensemble de lignes* et identifie les actions d’extraction. Il peut uniquement être utilisée sur les actions dont [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) a la valeur *cellules*.|  
|*Jeu de données*|Récupère un dataset.|  
|*Ensemble de lignes*|Récupère un ensemble de lignes.|  
|*Ligne de commande*|Exécute une commande à une invite de commandes.|  
|*Propriétaire*|Effectue une opération en utilisant une interface différente de celles répertoriées plus haut dans ce tableau.|  
|*Rapport*|Affiche une page qui varie selon le cas dans un navigateur Internet.<br /><br /> Cette valeur est identique à *Url* et identifie les actions de rapport.|  
  
 L’élément qui correspond au parent de **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données DrillThroughAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [Type de données ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

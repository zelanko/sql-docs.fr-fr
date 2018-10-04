---
title: Élément ProcessingQuery (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProcessingQuery Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProcessingQuery element
ms.assetid: d18e6f4b-c24c-4f73-8b85-4b6e8a82a695
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 055ec55609d60060385ebcce077119cf61549e1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051129"
---
# <a name="processingquery-element-assl"></a>Élément ProcessingQuery (ASSL)
  Contient le texte paramétrable de la requête à exécuter pour la notification d'état de traitement incrémentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<IncrementalProcessingNotification>  
   ...  
   <ProcessingQuery>...</ProcessingQuery>  
   ...  
</IncrementalProcessingNotification>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La table dans le [DataSourceView](../objects/datasourceview-element-assl.md) qui est référencé par le `ProcessingQuery` est identifié par l’élément frère, [TableID](id-element-assl.md).  
  
 L’élément qui correspond au parent de `ProcessingQuery` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

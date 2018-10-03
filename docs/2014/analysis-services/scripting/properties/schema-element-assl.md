---
title: Schema, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Schema Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Schema
helpviewer_keywords:
- Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b8f9ab11698c2e0e73436abb3506ca38c45afe6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218793"
---
# <a name="schema-element-assl"></a>Élément Schema (ASSL)
  Contient le schéma de la vue de source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|schéma|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataSourceView](../objects/datasourceview-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `Schema` est représenté à l'aide du format de DataSets XSD (XML Schema Definition) dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, avec quelques extensions pour les DataSets et d'autres extensions spécifiques à cette utilisation dans le langage de définition de données (DDL). Les DataSets définissent un mappage flexible de XSD à un schéma relationnel, mais renvoient ensuite les définitions de schéma XSD sous une forme plus canonique. Seule cette forme canonique est valide dans les sources de données.  
  
 L’élément qui correspond au parent de `Schema` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

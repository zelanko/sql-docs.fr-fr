---
title: Élément de schéma (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 130d1363a007fb51db3bc7b39efcae4d9140c368
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053399"
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
|Élément parent|[Élément DataSourceView](../objects/datasourceview-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `Schema` est représenté à l'aide du format de DataSets XSD (XML Schema Definition) dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, avec quelques extensions pour les DataSets et d'autres extensions spécifiques à cette utilisation dans le langage de définition de données (DDL). Les DataSets définissent un mappage flexible de XSD à un schéma relationnel, mais renvoient ensuite les définitions de schéma XSD sous une forme plus canonique. Seule cette forme canonique est valide dans les sources de données.  
  
 L’élément qui correspond au parent de `Schema` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
---
title: "Élément de schéma (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: Schema Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Schema
helpviewer_keywords: Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a39f50d6c91a8f4a321c62943e8894777c376faf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Élément DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **schéma** est représenté en utilisant le format de langage de définition de schéma XML (XSD) des jeux de données dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, avec certaines extensions pour les jeux de données spécifiques à cette utilisation dans le langage de définition de données (DDL). Les DataSets définissent un mappage flexible de XSD à un schéma relationnel, mais renvoient ensuite les définitions de schéma XSD sous une forme plus canonique. Seule cette forme canonique est valide dans les sources de données.  
  
 L’élément qui correspond au parent de **schéma** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

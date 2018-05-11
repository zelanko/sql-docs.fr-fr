---
title: Élément de schéma (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9822bbf6112673c5e03c382063af2ed017b8d5ca
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="schema-element-assl"></a>Élément Schema (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Type de données et longueur|Schéma|  
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
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

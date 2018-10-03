---
title: Élément Axis (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8587e1cdb0105d72d2bc0219c8d038ca0bd03ca4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153468"
---
# <a name="axis-element-xmla"></a>Élément Axis (XMLA)
  Contient un jeu de tuples utilisé pour représenter un axe unique dans un jeu de données multidimensionnel contenue par un [Axes](axes-element-xmla.md) élément qui utilise le [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) type de données, retourné par la [Execute](../xml-elements-methods-execute.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Axes>  
   ...  
   <Axis> <!-- when AxisFormat XMLA property is set to ClusterFormat -->  
      <CrossProduct>...</CrossProduct>  
   </Axis>  
   <Axis> <!-- when AxisFormat XMLA property is set to TupleFormat or CustomFormat -->  
      <Tuples>...</Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Axes](axes-element-xmla.md)|  
|Éléments enfants|[CrossProduct](crossproduct-element-xmla.md) ou [Tuples](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le contenu de l'élément `Axis` varie selon la valeur de la propriété XMLA `AxisFormat` utilisée par la méthode `Execute`.  
  
## <a name="tupleformat"></a>TupleFormat  
 Lorsqu’une application cliente définit le `AxisFormat` propriété *TupleFormat*, un axe est représenté comme un jeu de tuples. Chaque élément `Axis` contient un élément `Tuples` qui représente l'ensemble de tuples sur cet axe. Chaque tuple est représenté à l'aide d'un élément `Tuple` qui contient des éléments `Member` de chaque hiérarchie sur l'axe.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Lorsqu’une application cliente définit le `AxisFormat` propriété *ClusterFormat*, les membres sur chaque axe sont divisés en clusters dans lequel chaque cluster représente un produit croisé entre des ensembles ordonnés de membres de chaque hiérarchie. Chaque élément `Axis` consiste en un ou plusieurs éléments `CrossProduct`. Chaque élément `CrossProduct` contient un élément `Members` pour chaque hiérarchie sur l'axe.  
  
## <a name="customformat"></a>CustomFormat  
 Lorsqu’une application cliente définit le `AxisFormat` propriété *CustomFormat*, la valeur est traitée identique à la *TupleFormat* valeur par une instance d’Analysis Services.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre la structure de la `Axis` éléments lorsqu’un client spécifie *TupleFormat* ou *CustomFormat* pour le `AxisFormat` propriété XMLA suivantes membres de l’axe :  
  
|||||  
|-|-|-|-|  
|Hiérarchie `Time`|1999|1999|2000|  
|Hiérarchie `Category`|Réel|Budget|Budget|  
  
### <a name="code"></a>Code  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre la structure de la `Axis` éléments lorsqu’un client spécifie *ClusterFormat* pour le `AxisFormat` propriété XMLA les membres suivants de l’axe :  
  
||||||  
|-|-|-|-|-|  
|Hiérarchie `Time`|1999|1999|2000|2001|  
|Hiérarchie `Category`|Réel|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
### <a name="code"></a>Code  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

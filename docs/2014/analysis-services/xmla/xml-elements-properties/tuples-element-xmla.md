---
title: Élément tuples (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Tuples Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords:
- Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36f29edb149ab6a5c7c22dfe87c4d630289f29cd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128019"
---
# <a name="tuples-element-xmla"></a>Élément Tuples (XMLA)
  Contient un ensemble de [Tuple](tuple-element-xmla.md) des objets pour un [axe](axis-element-xmla.md) élément qui utilise le [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) type de données, retourné par la [Execute](../xml-elements-methods-execute.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Axis](axis-element-xmla.md)|  
|Éléments enfants|[Tuple](tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une application cliente définit le `AxisFormat` propriété *TupleFormat*, un axe est représenté comme un jeu de tuples. Chaque élément `Axis` contient un élément `Tuples` qui représente l'ensemble de tuples sur l'axe en question. Chaque tuple est représenté à l’aide un `Tuple` élément contenant [membre](member-element-xmla.md) éléments de chaque hiérarchie sur l’axe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la structure de la `Tuples` élément lorsqu’un client spécifie *TupleFormat* ou *CustomFormat* pour le `AxisFormat` XML pour la propriété Analysis (XMLA) Étant donné les membres suivants de l’axe :  
  
|||||  
|-|-|-|-|  
|Hiérarchie `Time`|1999|1999|2000|  
|Hiérarchie `Category`|Réel|Budget|Budget|  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

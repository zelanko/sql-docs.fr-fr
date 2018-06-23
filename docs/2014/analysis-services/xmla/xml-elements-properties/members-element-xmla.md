---
title: Élément Members (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5d812d0eea48c4f2b54352f61a176462b280071a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140598"
---
# <a name="members-element-xmla"></a>Élément Members (XMLA)
  Contient une collection de [membre](member-element-xmla.md) éléments contenus par le parent [CrossProduct](crossproduct-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
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
|Éléments parents|[CrossProduct](crossproduct-element-xmla.md)|  
|Éléments enfants|[Membre](member-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|Hierarchy|Requis `String` attribut. Nom de la hiérarchie dont font partie les membres que contient l'élément `Members`.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une application cliente définit le `AxisFormat` propriété *ClusterFormat*, les membres de chaque axe sont divisés en clusters dans lequel chaque cluster représente un produit croisé entre des ensembles ordonnés de membres de chaque hiérarchie. Chaque élément `Axis` consiste en un ou plusieurs éléments `CrossProduct`. Chaque élément `CrossProduct` contient un élément `Members` pour chaque hiérarchie sur l'axe. L'élément `Members`, à son tour, contient un élément `Member` pour chaque membre de la hiérarchie spécifiée inclus dans le produit croisé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la structure de la `Members` élément lorsqu’un client spécifie *ClusterFormat* pour le `AxisFormat` propriété XMLA les membres suivants de l’axe :  
  
||||||  
|-|-|-|-|-|  
|Hiérarchie `Time`|1999|1999|2000|2001|  
|Hiérarchie `Category`|Réel|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
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
  
  
---
title: Élément CrossProduct (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f67968b92fe879a6675222ed57306fca9a317b31
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="crossproduct-element-xmla"></a>Élément CrossProduct (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient un produit croisé entre des ensembles ordonnés de membres de chaque hiérarchie pour un [axe](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) élément qui utilise le [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) type de données retourné par la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Axe](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Éléments enfants|[Membres](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut| Description|  
|---------------|-----------------|  
|Taille|Requis **entier** attribut. Indique le nombre de tuples contenus dans le produit croisé représenté par le **CrossProduct** élément.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une application cliente définit le **AxisFormat** propriété *ClusterFormat*, les membres de chaque axe sont divisés en clusters dans lequel chaque cluster représente un produit croisé entre des ensembles ordonnés de membres de chaque hiérarchie. Chaque cluster est représenté par un **CrossProduct** élément. Chaque **CrossProduct** élément contient un **membres** , élément pour chaque hiérarchie sur l’axe. A **CrossProduct** élément peut contenir des membres d’une hiérarchie unique.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la structure de la **CrossProduct** élément lorsqu’un client spécifie *ClusterFormat* pour le **AxisFormat** propriété XMLA les membres suivants de l’axe :  
  
||||||  
|-|-|-|-|-|  
|Hiérarchie **Time**|1999|1999|2000|2001|  
|Hiérarchie **Category**|Réel|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
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
      <CrossProduct Size="1">  
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
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

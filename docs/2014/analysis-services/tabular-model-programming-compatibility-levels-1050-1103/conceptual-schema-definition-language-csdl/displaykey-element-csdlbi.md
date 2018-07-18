---
title: Élément DisplayKey (CSDLBI) | Microsoft Docs
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
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adcf9e8b2b87e0302158bbbf5652d8c32277170f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297149"
---
# <a name="displaykey-element-csdlbi"></a>Élément DisplayKey (CSDLBI)
  L'élément DisplayKey contient une liste des éléments suivants qui constituent ensemble un identificateur fort. DisplayKey existe uniquement en tant qu'enfant de l'élément EntityType. Il peut référencer des colonnes ou des fins de rôles.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les attributs de l'élément DisplayKey.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|non|True ou False|  
  
## <a name="remarks"></a>Notes  
 Cet élément est pour les rapports. L'élément auquel vous appliquez cet attribut n'a pas besoin d'être la clé de table réelle, seulement un élément que vous présenterez comme clé. Toutefois, la colonne utilisée pour l'élément DisplayKey doit contenir des valeurs uniques.  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple de code suivant, en CSDLBI version 1.1, illustre une colonne du modèle de données de l'exemple de base de données AdventureWorks qui a été désignée comme élément DisplayKey de la table.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un extrait de la représentation du cube Contoso Operations. Dans ce modèle, la colonne Color a été marquée en tant que clé d’affichage pour la table Bikes.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concepts CSDLBI](../csdlbi-concepts.md)  
  
  

---
title: "Élément NavigationProperty (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5b1af93e52bc1a2fbd95059c86f73a0481572399
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="navigationproperty-element-csdlbi"></a>Élément NavigationProperty (CSDLBI)
  L'élément NavigationProperty est un type complexe qui étend le type CSDL Member, pour prendre en charge les modèles de données Business Intelligence.  
  
> [!WARNING]  
>  Cet élément est destiné aux rapports et ne peut pas être modifié ou manipulé.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément NavigationProperty.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|Non|Nom au pluriel pour faire référence à un jeu d'instances de la propriété de navigation.<br /><br /> Si cet attribut est omis, l'attribut Caption du membre de base est utilisé.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L’exemple suivant illustre une propriété de navigation, en CSDLBI version 1.1, qui décrit le lien entre la table Product SubCategory et la table Product dans un modèle tabulaire.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant illustre une propriété de navigation, en CSDLBI version 1.1, qui décrit la relation entre deux tables dans le cube Contoso Operations. La relation connecte la table Bike Category et la table Product Subcategory.  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire au niveau de compatibilité 1050 1103 via des niveaux](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  


---
title: "Élément Hierarchy (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f3ff3c0bd93b75384b53e1f386a14196bcc803c3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchy-element-csdlbi"></a>Élément Hierarchy (CSDLBI)
  L'élément Hierarchy est un conteneur logique des champs d'une table qui peuvent être liés entre eux pour former une hiérarchie. L'élément Hierarchy est dérivé de l'élément CSDL Membre et a été étendu pour la prise en charge des hiérarchies créées dans des modèles de données Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Hierarchy.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Documentation|Non|Description de la hiérarchie.|  
|Niveau|Oui|Un ou plusieurs éléments Level qui définissent les colonnes utilisées dans la hiérarchie.<br /><br /> Consultez [Élément Level &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Notes  
 Dans les modèles tabulaires, les hiérarchies sont créées en spécifiant des relations parent-enfant entre des colonnes de la même table. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](../../../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.0, illustre une hiérarchie du modèle de données de l'exemple de base de données AdventureWorks qui a été ajoutée à la table Products.  
  
```  
  
<bi:Hierarchy Name="Categoryy">  
    <bi:Level Name="CategoryName">  
       <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
       </bi:Source>  
    </bi:Level>  
    <bi:Level Name="ProductName">  
       <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
       </bi:Source>  
    </bi:Level>  
</bi:Hierarchy>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre une hiérarchie cube Contoso Retail Operations.  
  
```  
  
<bi:Hierarchy Name="Product_Hierarchy" Caption="Product Hierarchy" ReferenceName="Product Hierarchy">  
   <bi:Documentation>  
      <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
   </bi:Documentation>  
  
   <bi:Level Name="ProductLine">  
      <bi:Source>  
      <bi:PropertyRef Name="ProductLine" />  
      </bi:Source>  
   </bi:Level>  
  
   <bi:Level Name="ModelName">  
         <bi:Source>  
      <bi:PropertyRef Name="ModelName" />  
      </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire au niveau de compatibilité 1050 1103 via des niveaux](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Fonctionnement des fonctions pour les hiérarchies Parent-enfant dans DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Configurer la &#40; Tous les &#41; Niveau de hiérarchies d’attributs](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  

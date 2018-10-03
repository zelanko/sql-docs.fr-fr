---
title: Élément Hierarchy (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 34ef944610a9e3b52fec600b3da5e1f9b06790bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129249"
---
# <a name="hierarchy-element-csdlbi"></a>Élément Hierarchy (CSDLBI)
  L'élément Hierarchy est un conteneur logique des champs d'une table qui peuvent être liés entre eux pour former une hiérarchie. L'élément Hierarchy est dérivé de l'élément CSDL Membre et a été étendu pour la prise en charge des hiérarchies créées dans des modèles de données Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Hierarchy.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Documentation|non|Description de la hiérarchie.|  
|Level|Oui|Un ou plusieurs éléments Level qui définissent les colonnes utilisées dans la hiérarchie.<br /><br /> Consultez [Élément Level &#40;CSDLBI&#41;](level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Notes  
 Dans les modèles tabulaires, les hiérarchies sont créées en spécifiant des relations parent-enfant entre des colonnes de la même table. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](../../tabular-models/hierarchies-ssas-tabular.md).  
  
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
 [Présentation du modèle d’objet tabulaire](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Fonctionnement des fonctions pour les hiérarchies Parent-enfant dans DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Configurer le &#40;tous les&#41; niveau hiérarchies d’attributs](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  

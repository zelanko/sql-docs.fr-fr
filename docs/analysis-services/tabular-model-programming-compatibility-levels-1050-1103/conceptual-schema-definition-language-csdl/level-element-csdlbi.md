---
title: "Niveau élément (CSDLBI) | Documents Microsoft"
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
applies_to: SQL Server 2016 Preview
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8430e055cb366420af51d8045381da1aacf78e3e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="level-element-csdlbi"></a>Élément Level (CSDLBI)
  L'élément Level est un type complexe qui définit un niveau unique dans une hiérarchie.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Level.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Source|Oui|Conteneur de la référence de la propriété.|  
|PropertyRef|Oui|Référence à une propriété d'instance. D'autres attributs de niveau, tels que captions, name et reference name, peuvent être pris dans la propriété de l'instance référencée. Par conséquent, vous n'avez pas besoin de les spécifier dans l'élément Level.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les hiérarchies dans les modèles tabulaires, consultez [Élément Hierarchy &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.1, affiche la définition de plusieurs niveaux dans une hiérarchie de l'exemple de modèle tabulaire AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
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
  
 L'exemple suivant, en CSDLBI version 1.1, illustre une hiérarchie à plusieurs niveaux, du cube Contoso Operations.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
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
  
  

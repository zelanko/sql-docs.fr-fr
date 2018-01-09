---
title: "L’élément DefaultDetails (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8010e9c0412b50c8d65a67c87c176bff02d1a887
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="defaultdetails-element-csdlbi"></a>Élément DefaultDetails (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]L’élément DefaultDetails représente une liste de références de propriété qui définissent ensemble le « champ de valeur par défaut de l’ensemble » des colonnes dans la table. Chaque propriété ne peut faire référence qu'à une mesure ou une colonne.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément DefaultDetails.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|non|Entier positif qui indique la présence et la position dans la collection.|  
  
## <a name="example"></a> Exemple  
 **Tabulaire**  
  
 L'extrait suivant, dans CSDLBI version 1.1, affiche un exemple de modèle de données AdventureWorks. Il u a un seul jeu de colonnes par défaut pour la table Employees (Title). Toutefois, trois colonnes ont été définies en tant qu'ensemble de champs par défaut pour la table Products.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a> Exemple  
 **(Multidimensionnel)**  
  
 L'extrait suivant, dans CSDLBI version 1.1, affiche la définition de la table Bike dans le cube Contoso Operations. Cette annotation indique si la colonne Color doit être affichée par défaut si aucune colonne d'affichage n'est spécifiée.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire au niveau de compatibilité 1050 1103 via des niveaux](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concepts CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  

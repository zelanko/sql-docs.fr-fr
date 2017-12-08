---
title: "L’élément DefaultDetails (CSDLBI) | Documents Microsoft"
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
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 25dafd209e16e820c6e0a70acb268d5c5d724f70
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="defaultdetails-element-csdlbi"></a>Élément DefaultDetails (CSDLBI)
  L'élément DefaultDetails représente une liste de références de propriété qui définissent l'« ensemble de champs par défaut » des colonnes de la table. Chaque propriété ne peut faire référence qu'à une mesure ou une colonne.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément DefaultDetails.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|Non|Entier positif qui indique la présence et la position dans la collection.|  
  
## <a name="example"></a>Exemple  
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
  
## <a name="example"></a>Exemple  
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
  
  

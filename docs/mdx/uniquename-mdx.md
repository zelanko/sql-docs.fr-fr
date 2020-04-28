---
title: UniqueName (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 69144341bd9cff344d4514f076517afac52e2a4b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097294"
---
# <a name="uniquename-mdx"></a>UniqueName (MDX)


  Retourne le nom unique d'une dimension, d'une hiérarchie, d'un niveau ou d'un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Dimension expression syntax  
Dimension_Expression.UniqueName  
  
Hierarchy expression syntax  
Hierarchy_Expression.UniqueName  
  
Level expression syntax  
Level_Expression.UniqueName  
  
Member expression syntax  
Member_Expression.UniqueName  
```  
  
## <a name="arguments"></a>Arguments  
 *Dimension_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui est résolue à une dimension.  
  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **UniqueName** retourne le nom unique de l’objet, et non le nom retourné par la fonction [Name](../mdx/name-mdx.md) . Le nom retourné n'inclut pas le nom du cube. Les résultats retournés dépendent des paramètres côté serveur ou de la propriété de chaîne de connexion UniqueNameStyle MDX.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur de nom unique de la dimension Product, de la hiérarchie Product Categories, du niveau Subcategory et du membre Bike Racks dans le cube Adventure Works.  
  
```  
WITH MEMBER DimensionUniqueName   
   AS [Product].UniqueName  
MEMBER HierarchyUniqueName   
   AS [Product].[Product Categories].UniqueName  
MEMBER LevelUniqueName   
   AS [Product].[Product Categories].[Subcategory].UniqueName  
MEMBER MemberUniqueName   
   AS [Product].[Product Categories].[Subcategory].[Bike Racks]  
SELECT   
   {DimensionUniqueName  
   , HierarchyUniqueName  
   , LevelUniqueName  
   , MemberUniqueName }  
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

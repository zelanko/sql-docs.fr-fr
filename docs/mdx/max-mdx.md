---
title: Max (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ad4bc2bf41caacbafb5bf36b5e95263ab2f85d22
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68098529"
---
# <a name="max-mdx"></a>Max (MDX)


  Retourne la valeur maximale d'une expression numérique évaluée sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Max( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, l'expression numérique spécifiée est évaluée sur le jeu, puis retourne la valeur maximale issue de cette évaluation. Si aucune expression numérique n'est spécifiée, le jeu spécifié est évalué dans le contexte actuel des membres du jeu, puis il retourne la valeur maximale issue de cette évaluation.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignore les valeurs NULL lors du calcul de la valeur maximale dans un jeu de nombres.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les ventes mensuelles maximales de chaque trimestre, sous-catégorie et chaque pays inscrit dans le cube Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Max   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  

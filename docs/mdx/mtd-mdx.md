---
title: MTD (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e604f66e48c8c8bb93ff5fd4abb174449f0fcdd9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088442"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  Retourne un jeu des membres frères de même niveau qu'un membre donné, commençant par le premier frère et se terminant par le membre donné, conformément à la contrainte du niveau Year de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si une expression de membre n’est pas spécifiée, la valeur par défaut est le membre actuel de la première hiérarchie avec un niveau de type *months* dans la première dimension de type *Time* dans le groupe de mesures.  
  
 La fonction **MTD** est une fonction de raccourci pour la fonction [PeriodsToDate](../mdx/periodstodate-mdx.md) lorsque la propriété type de la hiérarchie d’attribut sur laquelle un niveau est basé est définie sur *months*. Ce qui signifie que `Mtd(Member_Expression)` est équivalent à `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la somme du mois jusqu’à ce jour les coûts de fret pour les ventes sur Internet pour le mois de juillet, de 2002 à 20 juillet.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#41;MDX &#40;MDX](../mdx/sum-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

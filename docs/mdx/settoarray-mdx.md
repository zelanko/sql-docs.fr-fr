---
title: SetToArray (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c52c2641d21c20c91ec7548cafc969e506801b08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036992"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)


  Convertit un ou plusieurs jeux en tableau utilisé par une fonction définie par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction **SetToArray** convertit un ou plusieurs jeux en tableau à utiliser dans une fonction définie par l’utilisateur. Le nombre de dimensions de ce tableau est identique au nombre de jeux précisé.  
  
 L'expression numérique facultative peut fournir les valeurs des cellules du tableau. Si aucune expression numérique n'est spécifiée, la jointure croisée des jeux est évaluée dans le contexte actuel.  
  
 Les coordonnées des cellules du tableau obtenu correspondent à la position des jeux dans la liste. Soit par exemple trois jeux, `SA`, `SB` et `SC`. Chacun de ces jeux a deux éléments. L'instruction MDX, `SetToArray(SA, SB, SC)`, crée le tableau suivant en trois dimensions :  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Le type de retour de la fonction **SetToArray** est le type VARIANT, VT_ARRAY. Par conséquent, la sortie de la fonction **SetToArray** doit être utilisée uniquement en tant qu’entrée d’une fonction définie par l’utilisateur.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne un tableau.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

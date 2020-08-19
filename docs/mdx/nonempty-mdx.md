---
description: NonEmpty (MDX)
title: Non vide (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b887988327908f128633349de52f39a17d1e0978
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483722"
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)


  Retourne l'ensemble des tuples qui ne sont pas vides d'un jeu spécifié sur la base du produit croisé du jeu spécifié avec un deuxième jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Arguments  
 *set_expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *set_expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne dans le premier jeu spécifié les tuples qui ne sont pas vides lorsqu'ils sont évalués dans les tuples du deuxième jeu. La fonction non **vide** prend en compte les calculs et conserve les tuples dupliqués. Si aucun deuxième jeu n'est fourni, l'expression est évaluée dans le contexte des coordonnées actuelles des membres des hiérarchies d'attribut et des mesures du cube.  
  
> [!NOTE]  
>  Utilisez cette fonction plutôt que la fonction déconseillée [NonEmptyCrossjoin &#40;&#41;MDX ](../mdx/nonemptycrossjoin-mdx.md) .  
  
> [!IMPORTANT]  
>  La valeur non vide est une caractéristique des cellules référencées par les tuples, et non des tuples eux-mêmes.  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre un exemple simple de non **vide**, retournant tous les clients qui avaient une valeur non null pour le montant des ventes sur Internet le 1er juillet 2001 :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 L’exemple suivant retourne le jeu de tuples contenant les clients et les dates d’achat, à l’aide de la fonction **Filter** et des fonctions non **vides** pour rechercher la dernière date à laquelle chaque client a effectué un achat :  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;&#41;MDX de DefaultMember ](../mdx/defaultmember-mdx.md)   
 [Filtre &#40;&#41;MDX ](../mdx/filter-mdx.md)   
 [&#40;&#41;MDX de IsEmpty ](../mdx/isempty-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX ](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin&#41;MDX &#40;](../mdx/nonemptycrossjoin-mdx.md)  
  
  

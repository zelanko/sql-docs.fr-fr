---
title: Exists (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ba2cef1cfb95319cbe0aff827cb251ff7e2317c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68893608"
---
# <a name="exists-mdx"></a>Exists (MDX)


  Retourne l'ensemble des tuples du premier jeu spécifié qui coexistent avec un ou plusieurs tuples du deuxième jeu spécifié. Cette fonction effectue manuellement ce que l'auto-existence réalise de manière automatique. Pour plus d’informations sur la fonction auto Exists, consultez [concepts clés dans MDX &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
 Si le nom \<de groupe de mesures facultatif> est fourni, la fonction retourne des tuples qui existent avec un ou plusieurs tuples du deuxième jeu et les tuples qui ont des lignes associées dans la table de faits du groupe de mesures spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *MeasureGroupName*  
 Expression de chaîne valide qui précise le nom d'un groupe de mesures.  
  
## <a name="remarks"></a>Notes  
  
1.  Les lignes de groupe de mesures avec des mesures contenant des valeurs NULL contribuent à **existe** quand l’argument MeasureGroupName est spécifié. Il s’agit de la différence entre cette forme de EXISTS et la fonction non vide : si la propriété NullProcessing de ces mesures est définie sur Preserve, cela signifie que les mesures affichent des valeurs NULL lorsque les requêtes sont exécutées sur cette partie du cube ; Non Empty supprime toujours les tuples d’un jeu qui ont des valeurs de mesure null, tandis que Exists with the MeasureGroupName argument ne filtre pas les tuples qui ont des lignes de groupe de mesures associées, même si les valeurs de mesure sont null.  
  
2.  Si le paramètre *MeasureGroupName* est utilisé, les résultats dépendent de l’existence ou non de mesures visibles dans le groupe de mesures référencé ; s’il n’existe aucune mesure visible dans le groupe de mesures référencé, EXISTs retourne toujours un ensemble vide, quelles que soient les valeurs de *Set_Expression1* et *Set_Expression2*.  
  
## <a name="examples"></a>Exemples  
 Clients résidant en Californie :  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 Clients résidant en Californie avec ventes :  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Clients avec ventes :  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Clients ayant acheté des vélos :  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40;&#41;MDX](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin&#41;MDX &#40;](../mdx/nonemptycrossjoin-mdx.md)   
 [&#41;MDX &#40;non vide](../mdx/nonempty-mdx.md)   
 [&#40;&#41;MDX de IsEmpty](../mdx/isempty-mdx.md)  
  
  

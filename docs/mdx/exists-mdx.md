---
title: Existe (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b53932676cae30e4b1111c785a6a78c992a3685
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119590"
---
# <a name="exists-mdx"></a>Exists (MDX)


  Retourne l'ensemble des tuples du premier jeu spécifié qui coexistent avec un ou plusieurs tuples du deuxième jeu spécifié. Cette fonction effectue manuellement ce que l'auto-existence réalise de manière automatique. Pour plus d’informations sur automatique existe, consultez [Concepts clés dans MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 Si le paramètre facultatif \<nom de groupe de mesures > n’est fourni, la fonction retourne les tuples qui coexistent avec un ou plusieurs tuples à partir du deuxième jeu et les tuples qui sont associés à des lignes dans la table de faits du groupe de mesures spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *MeasureGroupName*  
 Expression de chaîne valide qui précise le nom d'un groupe de mesures.  
  
## <a name="remarks"></a>Notes  
  
1.  Lignes de groupe de mesures avec des mesures contenant des valeurs null contribuent à **Exists** lorsque l’argument MeasureGroupName est spécifié. Ceci est la différence entre cette forme de Exists et la fonction Nonempty : si la propriété NullProcessing de ces mesures est définie à conserver, cela signifie les mesures seront affiche des valeurs Null lorsque les requêtes sont exécutées sur cette partie du cube ; NonEmpty supprimera toujours les tuples à partir d’un jeu qui contient des valeurs de mesure Null, alors qu’Exists avec l’argument MeasureGroupName ne filtrera pas les tuples qui sont associés à des lignes de groupe de mesures, même si les valeurs de mesure sont Null.  
  
2.  Si *MeasureGroupName* paramètre est utilisé, résultats dépendront s’il existe des mesures visibles dans le groupe de mesures référencé ; s’il n’y aucune mesure visible dans le groupe de mesures référencé puis EXISTS retourne toujours un ensemble vide, indépendamment des valeurs de *Set_Expression1* et *Set_Expression2*.  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40;MDX&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40;MDX&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)  
  
  

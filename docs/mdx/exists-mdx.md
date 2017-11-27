---
title: Existe (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- Exists function
ms.assetid: 1e1d93b5-5be6-421c-b82b-839538ea50b1
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5483a7da135f6e486610d8a53e9dc23078a6cd3b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="exists-mdx"></a>Exists (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne l'ensemble des tuples du premier jeu spécifié qui coexistent avec un ou plusieurs tuples du deuxième jeu spécifié. Cette fonction effectue manuellement ce que l'auto-existence réalise de manière automatique. Pour plus d’informations sur automatique existe, consultez [Concepts clés dans MDX &#40; Analysis Services &#41; ](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
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
  
1.  Lignes de groupe de mesures avec des mesures contenant des valeurs null contribuent à **Exists** lorsque l’argument MeasureGroupName est spécifié. C'est la différence entre cette forme d'Exists et la fonction Nonempty : si la propriété NullProcessing de ces mesures est configurée sur Conserver, cela signifie que les mesures afficheront des valeurs NULL lorsque les requêtes sont exécutées contre cette partie du cube ; NonEmpty supprimera toujours des tuples d'un jeu qui a des valeurs de la mesure Null, alors qu'Exists avec l'argument MeasureGroupName ne filtrera pas les tuples qui ont des lignes de groupe de mesures associées, même si les valeurs de mesure sont Null.  
  
2.  Si *MeasureGroupName* paramètre est utilisé, s’il existe des mesures visibles dans le groupe de mesures référencé ; s’il en existe aucune mesure visible dans le groupe de mesures référencé puis EXISTS retourne toujours un jeu vide, indépendamment des valeurs de résultats dépend *Set_Expression1* et *Set_Expression2*.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Jointure croisée &#40; MDX &#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40; MDX &#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40; MDX &#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40; MDX &#41;](../mdx/isempty-mdx.md)  
  
  


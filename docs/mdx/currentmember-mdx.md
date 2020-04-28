---
title: CurrentMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 374a38d07c3174e799d01199e20e822f85deed13
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892920"
---
# <a name="currentmember-mdx"></a>CurrentMember (MDX)


  Retourne le membre actuel dans une hiérarchie spécifique au cours d'une itération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy_Expression.CurrentMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Au cours d'une itération effectuée dans un jeu de membres de hiérarchie, le membre manipulé à chaque étape de l'itération est le membre actuel. La fonction **CurrentMember** retourne ce membre.  
  
> [!IMPORTANT]  
>  Lorsqu'une dimension contient uniquement une hiérarchie visible unique, cette hiérarchie peut être désignée soit par le nom de dimension, soit par le nom de la hiérarchie, puisque le nom de dimension est résolu à son unique hiérarchie visible. Par exemple, `Measures.CurrentMember` est une expression MDX valide parce qu'elle est résolue à la seule hiérarchie de la dimension de mesures.  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre comment utiliser **CurrentMember** pour rechercher le membre actuel dans des hiérarchies sur les colonnes, les lignes et l’axe des secteurs :  
  
 `WITH MEMBER MEASURES.CURRENTDATE AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTPRODUCT AS`  
  
 `[Product].[Product Categories].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTMEASURE AS`  
  
 `MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTCUSTOMER AS`  
  
 `[Customer].[Customer Geography].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `[Product].[Product Categories].[Category].MEMBERS`  
  
 `*`  
  
 `{MEASURES.CURRENTDATE, MEASURES.CURRENTPRODUCT,MEASURES.CURRENTMEASURE, MEASURES.CURRENTCUSTOMER}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Customer].[Customer Geography].[Country].&[Australia])`  
  
 Le membre actuel change sur une hiérarchie utilisée sur un axe dans une requête. Par conséquent, le membre actuel sur d’autres hiérarchies de la même dimension qui ne sont pas utilisées sur un axe peut également changer ; ce comportement est appelé « auto-exist ». vous trouverez plus de détails dans les [concepts clés de MDX &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services). Par exemple, la requête suivante illustre comment le membre actuel sur la hiérarchie Année civile de la dimension Date change avec le membre actuel sur la hiérarchie Calendrier, lorsque celle-ci est affichée sur l'axe des lignes :  
  
 `WITH MEMBER MEASURES.CURRENTYEAR AS`  
  
 `[Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `{MEASURES.CURRENTYEAR}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 **CurrentMember** est très important pour faire en sorte que les calculs prennent en compte le contexte de la requête dans laquelle ils sont utilisés. L’exemple suivant retourne la quantité commandée de chaque produit et le pourcentage des quantités commandées par catégorie et par modèle, à partir du cube **Adventure Works** . La fonction **CurrentMember** identifie le produit dont la quantité commandée doit être utilisée pendant le calcul.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty  
(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

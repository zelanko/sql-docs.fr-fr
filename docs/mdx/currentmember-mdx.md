---
title: CurrentMember (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CURRENTMEMBER
dev_langs: kbMDX
helpviewer_keywords: CurrentMember function
ms.assetid: 5da76496-7d13-4f17-9cee-3e1ef70c2d97
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 2c8ff1f7343017b3c7870f963fe2006699f88e9d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="currentmember-mdx"></a>CurrentMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le membre actuel dans une hiérarchie spécifique au cours d'une itération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy_Expression.CurrentMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes   
 Au cours d'une itération effectuée dans un jeu de membres de hiérarchie, le membre manipulé à chaque étape de l'itération est le membre actuel. Le **CurrentMember** fonction retourne ce membre.  
  
> [!IMPORTANT]  
>  Lorsqu'une dimension contient uniquement une hiérarchie visible unique, cette hiérarchie peut être désignée soit par le nom de dimension, soit par le nom de la hiérarchie, puisque le nom de dimension est résolu à son unique hiérarchie visible. Par exemple, `Measures.CurrentMember` est une expression MDX valide parce qu'elle est résolue à la seule hiérarchie de la dimension de mesures.  
  
## <a name="examples"></a>Exemples  
 La requête suivante illustre comment **Currentmember** peut être utilisé pour rechercher le membre actuel dans les hiérarchies sur des colonnes, lignes et axe de secteur :  
  
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
  
 Le membre actuel change sur une hiérarchie utilisée sur un axe dans une requête. Par conséquent, le membre actuel sur d’autres hiérarchies sur la même dimension qui ne sont pas utilisés sur un axe peut également changer ; Ce comportement est appelé 'auto-existe', et vous trouverez plus de détails dans [Concepts clés dans MDX &#40; Analysis Services &#41; ](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Par exemple, la requête suivante illustre comment le membre actuel sur la hiérarchie Année civile de la dimension Date change avec le membre actuel sur la hiérarchie Calendrier, lorsque celle-ci est affichée sur l'axe des lignes :  
  
 `WITH MEMBER MEASURES.CURRENTYEAR AS`  
  
 `[Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `{MEASURES.CURRENTYEAR}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 **CurrentMember** est très important pour effectuer des calculs prenant en compte le contexte de la requête, ils sont utilisés dans. L’exemple suivant retourne la quantité commandée de chaque produit et le pourcentage des quantités commandées par catégorie et par modèle, à partir de la **Adventure Works** cube. Le **CurrentMember** fonction identifie le produit dont la quantité de commande doit être utilisée lors du calcul.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
